```
AdaptiveWNGradient <: DirectionUpdateRule
```

Represent an adaptive gradient method introduced by [GrapigliaStella:2023](@cite).

Given a positive threshold $\hat c \mathbb N$, an minimal bound $b_{\mathrm{min}} > 0$, an initial $b_0 ≥ b_{\mathrm{min}}$, and a gradient reduction factor threshold $\alpha ∈ [0,1)$.

Set $c_0=0$ and use $\omega_0 = \lVert \operatorname{grad} f(p_0) \rvert_{p_0}$.

For the first iterate use the initial step size $s_0 = \frac{1}{b_0}$.

Then, given the last gradient $X_{k-1} = \operatorname{grad} f(x_{k-1})$, and a previous $\omega_{k-1}$, the values $(b_k, \omega_k, c_k)$ are computed using $X_k = \operatorname{grad} f(p_k)$ and the following cases

If $\lVert X_k \rVert_{p_k} \leq \alpha\omega_{k-1}$, then let $\hat b_{k-1} ∈ [b_\mathrm{min},b_{k-1}]$ and set

$$
(b_k, \omega_k, c_k) = \begin{cases}
\bigl(\hat b_{k-1}, \lVert X_k\rVert_{p_k}, 0 \bigr) & \text{ if } c_{k-1}+1 = \hat c\\
\Bigl(b_{k-1} + \frac{\lVert X_k\rVert_{p_k}^2}{b_{k-1}}, \omega_{k-1}, c_{k-1}+1 \Bigr) & \text{ if } c_{k-1}+1<\hat c
\end{cases}
$$

If $\lVert X_k \rVert_{p_k} > \alpha\omega_{k-1}$, the set

$$
(b_k, \omega_k, c_k) =
\Bigl( b_{k-1} + \frac{\lVert X_k\rVert_{p_k}^2}{b_{k-1}}, \omega_{k-1}, 0)
$$

and return the step size $s_k = \frac{1}{b_k}$.

Note that for $α=0$ this is the Riemannian variant of `WNGRad`.

# Fields

  * `count_threshold::Int`: (`4`) an `Integer` for $\hat c$
  * `minimal_bound::Float64`: (`1e-4`) for $b_{\mathrm{min}}$
  * `alternate_bound::Function`: (`(bk, hat_c) -> min(gradient_bound, max(gradient_bound, bk/(3*hat_c)`) how to determine $\hat b_k$ as a function of `(bmin, bk, hat_c) -> hat_bk`
  * `gradient_reduction::Float64`: (`0.9`)
  * `gradient_bound` `norm(M, p0, grad_f(M,p0))` the bound $b_k$.

as well as the internal fields

  * `weight` for $ω_k$ initialised to $ω_0 =$`norm(M, p0, grad_f(M,p0))` if this is not zero, `1.0` otherwise.
  * `count` for the $c_k$, initialised to $c_0 = 0$.

# Constructor

```
AdaptiveWNGrad(M=DefaultManifold, grad_f=(M, p) -> zero_vector(M, rand(M)), p=rand(M); kwargs...)
```

Where all fields with defaults are keyword arguments and additional keyword arguments are

  * `adaptive`:   (`true`) switches the `gradient_reduction``α``to`0`.
  * `evaluation`: (`AllocatingEvaluation()`) specifies whether the gradient (that is used for initialisation only) is mutating or allocating
