```
curve = learning_curve(mach; resolution=30,
                             resampling=Holdout(),
                             repeats=1,
                             measure=default_measure(machine.model),
                             rows=nothing,
                             weights=nothing,
                             operation=nothing,
                             range=nothing,
                             acceleration=default_resource(),
                             acceleration_grid=CPU1(),
                             rngs=nothing,
                             rng_name=nothing)
```

与えられた教師あり機械 `mach` は、`range` で指定された単一のハイパーパラメータの関数として、パフォーマンス推定を生成するのに適したオブジェクトの名前付きタプルを返します。タプル `curve` には次のキーがあります: `:parameter_name`, `:parameter_scale`, `:parameter_values`, `:measurements`。

ランダム数生成器 (RNG) をハイパーパラメータとして持つ `model` の複数の曲線を生成するには、(おそらくネストされた) RNG フィールドの名前 `rng_name` と、各曲線用の RNG のベクトル `rngs` を指定します。あるいは、生成したい曲線の数に `rngs` を設定すると、その場合は RNG が自動的に生成されます。個々の曲線計算は、`acceleration=CPUProcesses()` または `acceleration=CPUThreads()` を使用して複数のプロセスに分散できます。以下の2番目の例でデモを参照してください。

```julia
X, y = @load_boston;
atom = @load RidgeRegressor pkg=MultivariateStats
ensemble = EnsembleModel(atom=atom, n=1000)
mach = machine(ensemble, X, y)
r_lambda = range(ensemble, :(atom.lambda), lower=10, upper=500, scale=:log10)
curve = learning_curve(mach; range=r_lambda, resampling=CV(), measure=mav)
using Plots
plot(curve.parameter_values,
     curve.measurements,
     xlab=curve.parameter_name,
     xscale=curve.parameter_scale,
     ylab = "CV estimate of RMS error")
```

`Holdout()` `resampling` 戦略を使用している場合（シャッフルなし）で、指定されたハイパーパラメータがいくつかの反復モデルにおける反復回数である場合（そのモデルが適切にオーバーロードされた `MLJModelInterface.update` メソッドを持っている場合）、パラメータの各増分ごとにトレーニングが最初から再開されることはありません。つまり、モデルは徐々にトレーニングされます。

```julia
atom.lambda=200
r_n = range(ensemble, :n, lower=1, upper=250)
curves = learning_curve(mach; range=r_n, verbosity=0, rng_name=:rng, rngs=3)
plot!(curves.parameter_values,
     curves.measurements,
     xlab=curves.parameter_name,
     ylab="Holdout estimate of RMS error")
```

```
learning_curve(model::Supervised, X, y; kwargs...)
learning_curve(model::Supervised, X, y, w; kwargs...)
```

マシンを最初に構築することなく、学習曲線（または曲線）を直接プロットします。

### キーワードオプションの概要

  * `resolution` - `range` から生成されるポイントの数（モデル評価の数）；デフォルトは `30`
  * `acceleration` - `evaluate!` に渡すための並列化オプション；`ComputationalResources.jl` の `CPU1`, `CPUProcesses` または `CPUThreads` のインスタンス；デフォルトは `default_resource()`
  * `acceleration_grid` - 各パフォーマンス評価を分散するための並列化オプション
  * `rngs` - モデルに渡すランダム数生成器を指定するためのもの（上記参照）
  * `rng_name` - ランダム数生成器を表すモデルのハイパーパラメータの名前（上記参照）；おそらくネストされている

その他のキーワードオプションは [`TunedModel`](@ref) に記載されています。
