# Ignite.jl

[![Dev](https://img.shields.io/badge/docs-dev-blue.svg)](https://jondeuce.github.io/Ignite.jl/dev/) [![Build Status](https://github.com/jondeuce/Ignite.jl/actions/workflows/CI.yml/badge.svg?branch=master)](https://github.com/jondeuce/Ignite.jl/actions/workflows/CI.yml?query=branch%3Amaster) [![Coverage](https://codecov.io/gh/jondeuce/Ignite.jl/branch/master/graph/badge.svg)](https://codecov.io/gh/jondeuce/Ignite.jl) [![Aqua QA](https://raw.githubusercontent.com/JuliaTesting/Aqua.jl/master/badge.svg)](https://github.com/JuliaTesting/Aqua.jl)

`Ignite.jl`へようこそ。これは、イベントとハンドラーを使用してニューラルネットワークのトレーニングと検証ループを簡素化するためのPythonライブラリ[`ignite`](https://github.com/pytorch/ignite)のJuliaポートです。

`Ignite.jl`はシンプルでありながら柔軟なエンジンとイベントシステムを提供し、アーティファクトの保存、メトリックのログ記録、モデルの検証など、さまざまなイベントを使用してトレーニングパイプラインを簡単に構成できます。イベントベースのトレーニングはトレーニングループを抽象化し、次のように置き換えます。

1. 単一のデータバッチを消費する*プロセス関数*をラップする*エンジン*、
2. 上記のデータバッチを生成する反復可能なデータローダー、そして
3. トレーニング中の特定のポイントで発火するように設定されたエンジンに添付されたイベントと対応するイベントハンドラー。

イベントハンドラーは、コールバックのような他のアプローチと比較してはるかに柔軟です：ハンドラーは任意の呼び出し可能なものであり、複数のハンドラーを単一のイベントに添付できます。複数のイベントが同じハンドラーをトリガーすることができ、トレーニング中のユーザー指定のポイントで発火するカスタムイベントを定義できます。これにより、トレーニングパイプラインに機能を追加することが容易になり、既存のコードを変更する必要が最小限に抑えられます。

## クイックスタート

以下の例は、`Ignite.jl`を使用してシンプルなニューラルネットワークをトレーニングする方法を示しています。注目すべき主な機能：

  * トレーニングステップはトレーニングループから分離されています：`train_step`プロセス関数はトレーニングデータのバッチを受け取り、トレーニング損失、勾配を計算し、モデルパラメータを更新します。
  * データローダーは任意の反復可能なコレクションであることができます。ここでは、[`MLUtils.jl`](https://github.com/JuliaML/MLUtils.jl)からの[`DataLoader`](https://juliaml.github.io/MLUtils.jl/stable/api/#MLUtils.DataLoader)を使用します。

```julia
using Ignite
using Flux, Zygote, Optimisers, MLUtils # ニューラルネットワークのトレーニング用

# シンプルなニューラルネットワークを構築し、Adamオプティマイザーを初期化
model = Chain(Dense(1 => 32, tanh), Dense(32 => 1))
optim = Flux.setup(Optimisers.Adam(1.0f-3), model)

# モックデータとデータローダーを作成
f(x) = 2x - x^3
xtrain, xtest = 2 * rand(Float32, 1, 10_000) .- 1, collect(reshape(range(-1.0f0, 1.0f0; length = 100), 1, :))
ytrain, ytest = f.(xtrain), f.(xtest)
train_data_loader = DataLoader((; x = xtrain, y = ytrain); batchsize = 64, shuffle = true, partial = false)
eval_data_loader = DataLoader((; x = xtest, y = ytest); batchsize = 10, shuffle = false)

# トレーニングエンジンを作成：
#   - `engine`は、以下で作成された親`trainer`エンジンへの参照です
#   - `batch`は、`train_data_loader`を反復することで取得されるトレーニングデータのバッチです
#   - （オプション）戻り値は`trainer.state.output`に格納されます
function train_step(engine, batch)
    x, y = batch
    l, gs = Zygote.withgradient(m -> sum(abs2, m(x) .- y), model)
    Optimisers.update!(optim, model, gs[1])
    return Dict("loss" => l)
end
trainer = Engine(train_step)

# トレーニングを開始
Ignite.run!(trainer, train_data_loader; max_epochs = 25, epoch_length = 100)
```

### 定期的にモデルを評価

`Ignite.jl`の真の力は、トレーニングエンジンに*イベントハンドラー*を追加することで発揮されます。

5回目のトレーニングエポックごとにモデルを評価しましょう。これは、上記のトレーニングコードを変更することなく簡単に組み込むことができます：

1. 評価データのバッチを消費する`evaluator`エンジンを作成します
2. 評価データのバッチにわたって評価メトリックの移動平均を蓄積する*イベントハンドラー*を`evaluator`エンジンに追加します。これを簡単にするために[`OnlineStats.jl`](https://github.com/joshday/OnlineStats.jl)を使用します。
3. トレーニングエポックごとに5回ごとに評価データローダーで`evaluator`を実行するイベントハンドラーを`trainer`に追加します。

```julia
using OnlineStats: Mean, fit!, value # 評価メトリックの追跡用

# `do`構文を使用して評価エンジンを作成：
evaluator = Engine() do engine, batch
    x, y = batch
    ypred = model(x) # 検証データの単一バッチでモデルを評価
    return Dict("ytrue" => y, "ypred" => ypred) # 結果は`evaluator.state.output`に格納されます
end

# メトリックを追跡するために評価エンジンにイベントハンドラーを追加：
add_event_handler!(evaluator, STARTED()) do engine
    # `evaluator`が開始されるとき、移動平均を初期化
    engine.state.metrics = Dict("abs_err" => Mean()) # 新しいフィールドは`engine.state`に動的に追加できます
end

add_event_handler!(evaluator, ITERATION_COMPLETED()) do engine
    # 各イテレーションで、予測から評価メトリックを計算
    o = engine.state.output
    m = engine.state.metrics["abs_err"]
    fit!(m, abs.(o["ytrue"] .- o["ypred"]) |> vec)
end

# 5エポックごとに`evaluator`を実行するイベントハンドラーを`trainer`に追加：
add_event_handler!(trainer, EPOCH_COMPLETED(; every = 5)) do engine
    Ignite.run!(evaluator, eval_data_loader)
    @info "評価メトリック: abs_err = $(evaluator.state.metrics["abs_err"])"
end

# 定期的な評価でトレーナーを実行
Ignite.run!(trainer, train_data_loader; max_epochs = 25, epoch_length = 100)
```

### 実行の終了

トレーニングの実行を完了する前に停止する方法はいくつかあります：

1. 通常通り例外をスローします。これにより、トレーニングが即座に停止します。その後、`EXCEPTION_RAISED()`イベントが発火します。
2. キーボード割り込みを使用します。つまり、`Ctrl+C`または`Cmd+C`を介して`InterruptException`をスローします。トレーニングは停止し、`INTERRUPT()`イベントが発火します。
3. [`Ignite.terminate!(trainer)`](https://jondeuce.github.io/Ignite.jl/dev/#Ignite.terminate!-Tuple{Engine})を介して優雅に終了するか、同等に`trainer.should_terminate = true`を使用します。これにより、現在のイテレーションが完了しますが、さらにイテレーションは開始されません。その後、`TERMINATE()`イベントが発火し、続いて`COMPLETED()`イベントが発火します。

### 早期停止

早期停止を実装するには、評価メトリックをチェックし、メトリックが改善されない場合に`trainer`を優雅に終了するイベントハンドラーを`trainer`に追加できます。そのために、まず[`Flux.early_stopping`](http://fluxml.ai/Flux.jl/stable/training/callbacks/#Flux.early_stopping)を使用してトレーニング終了トリガーを定義します：

```julia
# 評価損失が少なくとも`min_dist`だけ減少しない場合に
# 2回連続して`true`を返すコールバック
early_stop_trigger = Flux.early_stopping(2; init_score = Inf32, min_dist = 5.0f-3) do
    return value(evaluator.state.metrics["abs_err"])
end
```

次に、早期停止トリガーをチェックし、トリガーが`true`を返す場合にトレーニングを終了するイベントハンドラーを`trainer`に追加します：

```julia
# このハンドラーは、評価イベントハンドラーと同様に
# 毎回5エポックごとに発火する必要があります。
add_event_handler!(trainer, EPOCH_COMPLETED(; every = 5)) do engine
    if early_stop_trigger()
        @info "早期停止"
        Ignite.terminate!(trainer)
    end
end

# 定期的な評価と早期停止でトレーナーを実行
Ignite.run!(trainer, train_data_loader; max_epochs = 25, epoch_length = 100)
```

注意：新しいイベントを追加する代わりに、前のセクションの評価イベントハンドラーを変更して、`evaluator`が実行された後すぐに`early_stop_trigger()`をチェックすることもできます。

### アーティファクトの保存

アーティファクトのログ記録は、上記のコードを変更することなくトレーナーに簡単に追加できます。たとえば、10エポックごとに現在のモデルとオプティマイザーの状態をディスクに保存するには、[`JLD2.jl`](https://github.com/JuliaIO/JLD2.jl)を使用します：

```julia
using JLD2

# 10エポックごとにモデルとオプティマイザーの状態を保存
add_event_handler!(trainer, EPOCH_COMPLETED(; every = 10)) do engine
    model_state = Flux.state(model)
    jldsave("model_and_optim.jld2"; model_state, optim)
    @info "モデルとオプティマイザーの状態をディスクに保存しました"
end
```

### イベントごとに複数の関数をトリガー

同じイベントに複数のイベントハンドラーを追加できます：

```julia
add_event_handler!(trainer, COMPLETED()) do engine
    # トレーニングが完了した後に実行されます
end
add_event_handler!(trainer, COMPLETED()) do engine
    # トレーニングが完了した後に、上記の関数の後に実行されます
end
```

### 複数のイベントに同じハンドラーを添付

ブール演算子`|`と`&`を使用してイベントを組み合わせることができます：

```julia
add_event_handler!(trainer, EPOCH_COMPLETED(; every = 10) | COMPLETED()) do engine
    # 毎回10エポックの終わり、またはトレーニングが完了したときに実行されます
end

throttled_event = EPOCH_COMPLETED(; every = 3) & EPOCH_COMPLETED(; event_filter = throttle_filter(30.0))
add_event_handler!(trainer, throttled_event) do engine
    # 最後の発火から30秒以上経過している場合、毎回3エポックの終わりに実行されます
end
```

### カスタムイベントの定義

カスタムイベントを作成し、トレーニングプロセスのユーザー定義の段階で発火させることができます。

たとえば、バックワードパスとオプティマイザーステップの開始と終了で発火するイベントを定義したいとします。必要なのは、`AbstractLoopEvent`をサブタイプ化する新しいイベントタイプを定義し、次に`train_step`プロセス関数内の適切なポイントで`fire_event!`を使用してそれらを発火させることだけです：

```julia
struct BACKWARD_STARTED <: AbstractLoopEvent end
struct BACKWARD_COMPLETED <: AbstractLoopEvent end
struct OPTIM_STEP_STARTED <: AbstractLoopEvent end
struct OPTIM_STEP_COMPLETED <: AbstractLoopEvent end

function train_step(engine, batch)
    x, y = batch

    # モデルに対する損失の勾配を計算
    fire_event!(engine, BACKWARD_STARTED())
    l, gs = Zygote.withgradient(m -> sum(abs2, m(x) .- y), model)
    engine.state.gradients = gs # エンジンの状態はイベントハンドラーによってアクセスできます
    fire_event!(engine, BACKWARD_COMPLETED())

    # モデルのパラメータを更新
    fire_event!(engine, OPTIM_STEP_STARTED())
    Optimisers.update!(optim, model, gs[1])
    fire_event!(engine, OPTIM_STEP_COMPLETED())

    return Dict("loss" => l)
end
trainer = Engine(train_step)
```

次に、これらのカスタムイベントのためのイベントハンドラーを通常通り追加します：

```julia
add_event_handler!(trainer, BACKWARD_COMPLETED(; every = 10)) do engine
    # 10回目のバックワードパスが完了した後にこのコードが実行されます
end
```

---

*このページは、[Literate.jl](https://github.com/fredrikekre/Literate.jl)を使用して生成されました。*
