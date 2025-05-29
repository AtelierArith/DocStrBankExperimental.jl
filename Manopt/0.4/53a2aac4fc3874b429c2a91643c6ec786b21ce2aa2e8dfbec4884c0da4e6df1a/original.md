```
Nesterov <: DirectionUpdateRule
```

## Fields

  * `γ`
  * `μ` the strong convexity coefficient
  * `v` (=$=v_k$, $v_0=x_0$) an interim point to compute the next gradient evaluation point `y_k`
  * `shrinkage` (`= i -> 0.8`) a function to compute the shrinkage $β_k$ per iterate.

Assume $f$ is $L$-Lipschitz and $μ$-strongly convex. Given

  * a step size $h_k<\frac{1}{L}$ (from the [`GradientDescentState`](@ref)
  * a `shrinkage` parameter $β_k$
  * and a current iterate $x_k$
  * as well as the interim values $γ_k$ and $v_k$ from the previous iterate.

This compute a Nesterov type update using the following steps, see [ZhangSra:2018](@cite)

1. Compute the positive root $α_k∈(0,1)$ of $α^2 = h_k\bigl((1-α_k)γ_k+α_k μ\bigr)$.
2. Set $\bar γ_k+1 = (1-α_k)γ_k + α_kμ$
3. $y_k = \operatorname{retr}_{x_k}\Bigl(\frac{α_kγ_k}{γ_k + α_kμ}\operatorname{retr}^{-1}_{x_k}v_k \Bigr)$
4. $x_{k+1} = \operatorname{retr}_{y_k}(-h_k \operatorname{grad}f(y_k))$
5. $v_{k+1} = `\operatorname{retr}_{y_k}\Bigl(\frac{(1-α_k)γ_k}{\barγ_k}\operatorname{retr}_{y_k}^{-1}(v_k) - \frac{α_k}{\bar γ_{k+1}}\operatorname{grad}f(y_k) \Bigr)$
6. $γ_{k+1} = \frac{1}{1+β_k}\bar γ_{k+1}$

Then the direction from $x_k$ to $x_k+1$ by $d = \operatorname{retr}^{-1}_{x_k}x_{k+1}$ is returned.

# Constructor

```
Nesterov(M::AbstractManifold, p::P; γ=0.001, μ=0.9, shrinkage = k -> 0.8;
    inverse_retraction_method=LogarithmicInverseRetraction())
```

Initialize the Nesterov acceleration, where `x0` initializes `v`.
