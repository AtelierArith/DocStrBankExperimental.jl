```
StateEstimationProblem(model, inputs, outputs; disturbance_inputs, discretization, Ts, df, dg, x0map=[], pmap=[])
```

状態推定問題を表す構造体。

## 引数:

  * `model`: MTK ODESystem モデル。このモデルは構造的簡略化を受けてはならない。
  * `inputs`: 動的システムへの入力。`@variables` 型の記号変数のベクトルでなければならない。
  * `outputs`: 動的システムの出力。`@variables` 型の記号変数のベクトルでなければならない。
  * `disturbance_inputs`: 動的システムへの外乱入力。`@variables` 型の記号変数のベクトルでなければならない。これらの外乱入力は、動的ノイズ $w$ がシステムに入る場所を示す。確率分布 $d_f$ はこれらの変数に対して定義される。
  * `discretization`: 連続時間動的関数 `f_cont(x,u,p,t)` を取り、離散時間動的関数 `f_disc(x,u,p,t)` を返す関数 `discretization(f_cont, Ts, ndiff, nalg, nu) = f_disc`。`ndiff` は微分状態変数の数、`nalg` は代数変数の数、`nu` は入力の数である。
  * `Ts`: 離散化の時間ステップ。
  * `df`: 動的ノイズ $w$ の確率分布。カルマン型推定器を使用する場合、これは `MvNormal` または `SimpleMvNormal` 分布でなければならない。
  * `dg`: 測定ノイズ $e$ の確率分布。カルマン型推定器を使用する場合、これは `MvNormal` または `SimpleMvNormal` 分布でなければならない。
  * `x0map`: 記号変数をその初期値にマッピングする辞書。変数が提供されていない場合、それはゼロに初期化されると見なされる。値はスカラー数である場合、初期状態の共分散は `σ0^2*I(nx)` に設定され、値が `Distributions.Normal` である場合、提供された分布が初期状態の分布として使用される。分布を渡す場合、すべての状態変数に値が提供されなければならない。
  * `σ0`: 初期状態の標準偏差。これは `x0map` が提供されていない場合、または `x0map` の値がスカラーである場合に使用される。
  * `pmap`: 記号変数をその値にマッピングする辞書。変数が提供されていない場合、それはゼロに初期化されると見なされる。

## 使用法:

擬似コード

```julia
prob      = StateEstimationProblem(...)
kf        = get_filter(prob, ExtendedKalmanFilter)      # または UnscentedKalmanFilter
filtersol = forward_trajectory(kf, u, y)
sol       = StateEstimationSolution(filtersol, prob)   # 高レベルの解オブジェクトにパッケージ化
plot(sol, idxs=[prob.state; prob.outputs; prob.inputs]) # 解をプロット
```
