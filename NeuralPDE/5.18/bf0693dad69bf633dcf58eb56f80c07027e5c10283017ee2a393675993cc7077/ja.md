```
ahmc_bayesian_pinn_ode(prob, chain; strategy = GridTraining, dataset = [nothing],
                       init_params = nothing, draw_samples = 1000, physdt = 1 / 20.0f0,
                       l2std = [0.05], phystd = [0.05], phynewstd = [0.05], priorsNNw = (0.0, 2.0),
                       param = [], nchains = 1, autodiff = false, Kernel = HMC,
                       Adaptorkwargs = (Adaptor = StanHMCAdaptor,
                           Metric = DiagEuclideanMetric, targetacceptancerate = 0.8),
                       Integratorkwargs = (Integrator = Leapfrog,),
                       MCMCkwargs = (n_leapfrog = 30,), progress = false,
                       verbose = false)
```

!!! warn
    `ahmc_bayesian_pinn_ode()` は、`du = f(u,p,t)` の形で書かれたODEのみをサポートしており、`f(du,u,p,t)` ではありません。アウトオブプレイスとして宣言されていない場合、`ahmc_bayesian_pinn_ode()` はエラーで終了します。


## 例

```julia
linear = (u, p, t) -> -u / p[1] + exp(t / p[2]) * cos(t)
tspan = (0.0, 10.0)
u0 = 0.0
p = [5.0, -5.0]
prob = ODEProblem(linear, u0, tspan, p)

### データセットの作成（正確なパラメータ推定のための必要性）
sol = solve(prob, Tsit5(); saveat = 0.05)
u = sol.u[1:100]
time = sol.t[1:100]

### データセットとBPINNの作成
x̂ = collect(Float64, Array(u) + 0.05 * randn(size(u)))
dataset = [x̂, time]

chain1 = Lux.Chain(Lux.Dense(1, 5, tanh), Lux.Dense(5, 5, tanh), Lux.Dense(5, 1)

### ここではODEを単純に解決しているため、データセットを渡さない方が良い（probで指定されたODEパラメータを使用）
fh_mcmc_chain1, fhsamples1, fhstats1 = ahmc_bayesian_pinn_ode(prob, chain1,
                                                            dataset = dataset,
                                                            draw_samples = 1500,
                                                            l2std = [0.05],
                                                            phystd = [0.05],
                                                            priorsNNw = (0.0,3.0))

### ODEを解決し、パラメータを推定するため、パラメータを最適化するためにデータセットが必要 + ODEパラメータの事前分布
fh_mcmc_chain2, fhsamples2, fhstats2 = ahmc_bayesian_pinn_ode(prob, chain1,
                                                            dataset = dataset,
                                                            draw_samples = 1500,
                                                            l2std = [0.05],
                                                            phystd = [0.05],
                                                            priorsNNw = (0.0,3.0),
                                                            param = [Normal(6.5,0.5), Normal(-3,0.5)])
```

## 注意事項

データセットは正確なパラメータ推定と方程式の解決に必要です。方程式の解決のみを行う場合は、データセットを提供しないでください。

## 位置引数

  * `prob`: DEProblem（アウトオブプレイスで、関数のシグネチャは f(u,p,t) である必要があります）。
  * `chain`: ベイジアンPINNを作成するLuxニューラルネットワーク。

## キーワード引数

  * `strategy`: 評価のためのポイントを選択するために使用されるトレーニング戦略。デフォルトでは、指定されたphysdtの離散化を使用したGridTrainingが使用されます。
  * `init_params`: BPINNの初期パラメータ値（理想的には複数のチェーンに対して異なる初期化が推奨されます）
  * `nchains`: サンプリングしたいチェーンの数
  * `draw_samples`: MCMCアルゴリズムで引き出されるサンプルの数（ウォームアップサンプルは引き出しサンプルの約2/3です）
  * `l2std`: L2損失/データセットに対するBPINN予測の標準偏差
  * `phystd`: 選択された基礎ODEシステムに対するBPINN予測の標準偏差
  * `phynewstd`: 新しい損失関数項の標準偏差
  * `priorsNNw`: BPINNネットワークパラメータのための（平均、標準偏差）のタプル。BPINNの重みとバイアスはデフォルトで正規分布です。
  * `param`: 逆問題の場合に選択されたODEパラメータ分布のベクトル。
  * `autodiff`: 微分バックエンドの選択のためのブール値（デフォルトは数値）
  * `physdt`: ODEを時間領域で近似するためのタイムステップ。（デフォルトは1/20.0）
  * `Kernel`: MCMCサンプリングアルゴリズムの選択（AdvancedHMC.jlの実装 HMC/NUTS/HMCDA）
  * `Integratorkwargs`: `Integrator`, `jitter_rate`, `tempering_rate`。参照: https://turinglang.org/AdvancedHMC.jl/stable/
  * `Adaptorkwargs`: `Adaptor`, `Metric`, `targetacceptancerate`。参照: https://turinglang.org/AdvancedHMC.jl/stable/ 注意: 提案が受け入れられる反復のターゲットパーセンテージ（小数で、デフォルトは0.8）
  * `MCMCargs`: 選択されたMCMCカーネル（HMC/NUTS/HMCDA）のすべての引数を含むNamedTuple、次のようになります：

      * `n_leapfrog`: HMCのためのリープフロッグステップの数
      * `δ`: NUTSおよびHMCDAのためのターゲット受け入れ確率
      * `λ`: HMCDAのためのターゲット軌道長
      * `max_depth`: 最大倍増ツリー深度（NUTS）
      * `Δ_max`: 倍増ツリー中の最大発散（NUTS）

    参照: https://turinglang.org/AdvancedHMC.jl/stable/
  * `progress`: 進捗メーターを表示するかどうかを制御します。
  * `verbose`: 詳細度を制御します。（AHMCでのサンプル呼び出し引数）

!!! warning
    AdvancedHMC.jlはまだ便利な構造体を開発中であり、新しいリリースで変更が必要になる可能性があります。

