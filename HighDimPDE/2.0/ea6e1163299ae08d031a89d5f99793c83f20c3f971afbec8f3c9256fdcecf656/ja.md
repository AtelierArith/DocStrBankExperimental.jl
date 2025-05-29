```julia
ParabolicPDEProblem(
    μ,
    σ,
    x0,
    tspan;
    g,
    f,
    p,
    xspan,
    x0_sample,
    neumann_bc,
    payoff,
    kw...
)

```

パラボリック偏微分方程式の定義は次の形式です：

$$
\begin{aligned}
    \frac{du}{dt} &= \tfrac{1}{2} \text{Tr}(\sigma \sigma^T) \Delta u(x, t) + \mu \nabla u(x, t) \\
    &\quad +  f(x, u(x, t), ( \nabla_x u )(x, t), p, t)
\end{aligned}
$$

  * 半線形パラボリック偏微分方程式 

      * f -> f(X, u, σᵀ∇u, p, t)
  * コルモゴロフ微分方程式

      * f -> `nothing`
      * x0 -> nothing, xspan は提供されなければなりません。
  * 障害物偏微分方程式 

      * f -> `nothing`
      * g -> `nothing`
      * 割引ペイオフ関数が提供されます。

## 引数

  * `μ` : ドリフト関数、形式は `μ(x, p, t)`。
  * `σ` : 拡散関数 `σ(x, p, t)`。
  * `x`: `u(x,t)` が近似される点。`x0_sample` が提供されている場合でも必要です。PDEの次元を決定します。
  * `tspan`: 問題の時間範囲。
  * `g` : 初期条件、形式は `g(x, p, t)`。
  * `f` : 非線形関数、形式は `f(X, u, σᵀ∇u, p, t)`

## オプション引数

  * `p`: パラメータベクトル。
  * `x0_sample` : `x0` のサンプリング方法。`UniformSampling(a,b)`、`NormalSampling(σ_sampling, shifted)`、またはデフォルトの `NoSampling` です。`NoSampling` の場合、単一の点 `x` でのみ解が評価されます。
  * `neumann_bc`: 提供される場合、ハイパーキューブ `neumann_bc[1] × neumann_bc[2]` に対するノイマン境界条件。
  * `xspan`: 独立変数 `x` の範囲
  * `payoff`: 割引ペイオフ関数。最適停止問題（障害物PDE）の解決時に必要です。
