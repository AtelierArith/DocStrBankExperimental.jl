```
BNNODE(chain, kernel = HMC; strategy = nothing, draw_samples = 2000,
       priorsNNw = (0.0, 2.0), param = [nothing], l2std = [0.05],
       phystd = [0.05], phynewstd = [0.05], dataset = [nothing], physdt = 1 / 20.0,
       MCMCargs = (; n_leapfrog=30), nchains = 1, init_params = nothing,
       Adaptorkwargs = (; Adaptor = StanHMCAdaptor, targetacceptancerate = 0.8,
                          Metric = DiagEuclideanMetric),
       Integratorkwargs = (Integrator = Leapfrog,), autodiff = false,
       progress = false, verbose = false)
```

常微分方程を解くためのアルゴリズムで、ベイジアンニューラルネットワークを使用しています。これは、標準の `ODEProblem` のソルバーとして使用される物理インフォームドニューラルネットワークの特殊化です。

!!! warn
    BNNODEは、`du = f(u,p,t)` の形で書かれたODEのみをサポートしていることに注意してください。`f(du,u,p,t)` の形ではありません。アウトオブプレースとして宣言されていない場合、BNNODEはエラーで終了します。


## 位置引数

  * `chain`: `Lux.AbstractLuxLayer` として定義されたニューラルネットワークアーキテクチャ。
  * `kernel`: MCMCサンプリングアルゴリズムの選択。デフォルトは `AdvancedHMC.HMC`

## キーワード引数

(`NeuralPDE.ahmc_bayesian_pinn_ode` のキーワード引数を参照してください。)

## 例

```julia
linear = (u, p, t) -> -u / p[1] + exp(t / p[2]) * cos(t)
tspan = (0.0, 10.0)
u0 = 0.0
p = [5.0, -5.0]
prob = ODEProblem(linear, u0, tspan, p)
linear_analytic = (u0, p, t) -> exp(-t / 5) * (u0 + sin(t))

sol = solve(prob, Tsit5(); saveat = 0.05)
u = sol.u[1:100]
time = sol.t[1:100]
x̂ = u .+ (u .* 0.2) .* randn(size(u))
dataset = [x̂, time]

chainlux = Lux.Chain(Lux.Dense(1, 6, tanh), Lux.Dense(6, 6, tanh), Lux.Dense(6, 1))

alg = BNNODE(chainlux; draw_samples = 2000, l2std = [0.05], phystd = [0.05],
             priorsNNw = (0.0, 3.0), progress = true)

sol_lux = solve(prob, alg)

# パラメータ推定を伴う
alg = BNNODE(chainlux; dataset, draw_samples = 2000, l2std = [0.05], phystd = [0.05],
             priorsNNw = (0.0, 10.0), param = [Normal(6.5, 0.5), Normal(-3, 0.5)],
             progress = true)

sol_lux_pestim = solve(prob, alg)
```

## 解のノート

解は、選択された戦略に従って固定された時間点で評価されることに注意してください。アンサンブル解は、`saveat` のステップで評価され、提供されます。データセットは、ODEパラメータ推定が行われているときにのみ提供されるべきです。ニューラルネットワークは完全に連続的な解であるため、`BPINNsolution` は正確な補間です（ニューラルネットワークのトレーニング結果に基づく）。さらに、`BPINNstats` は `sol.fullsolution` として返され、さらなる分析に使用されます。

## 参考文献

Liu Yanga, Xuhui Menga, George Em Karniadakis. "B-PINNs: Bayesian Physics-Informed Neural Networks for Forward and Inverse PDE Problems with Noisy Data".

Kevin Linka, Amelie Schäfer, Xuhui Meng, Zongren Zou, George Em Karniadakis, Ellen Kuhl "Bayesian Physics Informed Neural Networks for real-world nonlinear dynamical systems".
