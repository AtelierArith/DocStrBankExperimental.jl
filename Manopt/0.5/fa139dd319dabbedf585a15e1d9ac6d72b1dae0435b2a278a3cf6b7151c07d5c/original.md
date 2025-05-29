```
AdaptiveWNGradient(; kwargs...)
AdaptiveWNGradient(M::AbstractManifold; kwargs...)
```

A stepsize based on the adaptive gradient method introduced by [GrapigliaStella:2023](@cite).

Given a positive threshold $\hat{c} ∈ ℕ$, an minimal bound $b_{\text{min}} > 0$, an initial $b_0 ≥ b_{\text{min}}$, and a gradient reduction factor threshold $α ∈ [0,1)$.

Set $c_0=0$ and use $ω_0 = \lVert \operatorname{grad} f(p_0) \rVert_{p_0}$.

For the first iterate use the initial step size $s_0 = \frac{1}{b_0}$.

Then, given the last gradient $X_{k-1} = \operatorname{grad} f(x_{k-1})$, and a previous $ω_{k-1}$, the values $(b_k, ω_k, c_k)$ are computed using $X_k = \operatorname{grad} f(p_k)$ and the following cases

If $\lVert X_k \rVert_{p_k} ≤ αω_{k-1}$, then let $\hat{b}_{k-1} ∈ [b_{\text{min}},b_{k-1}]$ and set

$$
(b_k, ω_k, c_k) = \begin{cases}   \bigl(\hat{b}_{k-1}, \lVert X_k \rVert_{p_k}, 0 \bigr) & \text{ if } c_{k-1}+1 = \hat{c}\\\\    \bigl( b_{k-1} + \frac{\lVert X_k \rVert_{p_k}^2}{b_{k-1}}, ω_{k-1}, c_{k-1}+1 \Bigr) & \text{ if } c_{k-1}+1<\hat{c}\end{cases}
$$

If $\lVert X_k \rVert_{p_k} > αω_{k-1}$, the set

$$
(b_k, ω_k, c_k) = \Bigl( b_{k-1} + \frac{\lVert X_k \rVert_{p_k}^2}{b_{k-1}}, ω_{k-1}, 0 \Bigr)
$$

and return the step size $s_k = \frac{1}{b_k}$.

Note that for $α=0$ this is the Riemannian variant of `WNGRad`.

## Keyword arguments

  * `adaptive=true`: switches the `gradient_reduction``α``(if`true`) to`0`.
  * `alternate_bound = (bk, hat_c) ->  min(gradient_bound == 0 ? 1.0 : gradient_bound, max(minimal_bound, bk / (3 * hat_c))`: how to determine $\hat{k}_k$ as a function of `(bmin, bk, hat_c) -> hat_bk`
  * `count_threshold=4`:  an `Integer` for $\hat{c}$
  * `gradient_reduction::R=adaptive ? 0.9 : 0.0`: the gradient reduction factor threshold $α ∈ [0,1)$
  * `gradient_bound=norm(M, p, X)`: the bound $b_k$.
  * `minimal_bound=1e-4`: the value $b_{\text{min}}$
  * `p=`[`rand`](@extref Base.rand-Tuple{AbstractManifold})`(M)`: a point on the manifold $\mathcal M$only used to define the `gradient_bound`
  * `X=`[`zero_vector`](@extref `ManifoldsBase.zero_vector-Tuple{AbstractManifold, Any}`)`(M, p)`: a tangent vector at the point $p$ on the manifold $\mathcal M$only used to define the `gradient_bound`
