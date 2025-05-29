```julia
PIDEProblem(
    μ,
    σ,
    x0,
    tspan,
    g,
    f;
    p,
    x0_sample,
    neumann_bc,
    kw...
)

```

部分積分微分問題を定義します。形式は次の通りです。

$$
\begin{aligned}
    \frac{du}{dt} &= \tfrac{1}{2} \text{Tr}(\sigma \sigma^T) \Delta u(x, t) + \mu \nabla u(x, t) \\
    &\quad + \int f(x, y, u(x, t), u(y, t), ( \nabla_x u )(x, t), ( \nabla_x u )(y, t), p, t) dy,
\end{aligned}
$$

初期条件は $u(x,0) = g(x)$ です。

## 引数

  * `g` : 初期条件、形式は `g(x, p, t)`。
  * `f` : 非線形関数、形式は `f(x, y, u(x, t), u(y, t), ∇u(x, t), ∇u(y, t), p, t)`。
  * `μ` : ドリフト関数、形式は `μ(x, p, t)`。
  * `σ` : 拡散関数 `σ(x, p, t)`。
  * `x`: `u(x,t)` が近似される点。`x0_sample` が提供されている場合でも必要です。PDEの次元を決定します。
  * `tspan`: 問題の時間範囲。
  * `p`: パラメータベクトル。
  * `x0_sample` : `x0` のサンプリング方法。`UniformSampling(a,b)`、`NormalSampling(σ_sampling, shifted)`、またはデフォルトの `NoSampling` のいずれかです。`NoSampling` の場合、単一の点 `x` でのみ解が評価されます。
  * `neumann_bc`: 提供されている場合、ハイパーキューブ `neumann_bc[1] × neumann_bc[2]` に対するノイマン境界条件。
