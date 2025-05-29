```
Nesterov(; kwargs...)
Nesterov(M::AbstractManifold; kwargs...)
```

Assume $f$ is $L$-Lipschitz and $μ$-strongly convex. Given

  * a step size $h_k<\frac{1}{L}$ (from the [`GradientDescentState`](@ref)
  * a `shrinkage` parameter $β_k$
  * and a current iterate $p_k$
  * as well as the interim values $γ_k$ and $v_k$ from the previous iterate.

This compute a Nesterov type update using the following steps, see [ZhangSra:2018](@cite)

1. Compute the positive root $α_k∈(0,1)$ of $α^2 = h_k\bigl((1-α_k)γ_k+α_k μ\bigr)$.
2. Set $\barγ_k+1 = (1-α_k)γ_k + α_kμ$
3. $y_k = \operatorname{retr}_{p_k}\Bigl(\frac{α_kγ_k}{γ_k + α_kμ}\operatorname{retr}^{-1}_{p_k}v_k \Bigr)$
4. $x_{k+1} = \operatorname{retr}_{y_k}(-h_k \operatorname{grad}f(y_k))$
5. $v_{k+1} = \operatorname{retr}_{y_k}\Bigl(\frac{(1-α_k)γ_k}{\barγ_k}\operatorname{retr}_{y_k}^{-1}(v_k) - \frac{α_k}{\barγ_{k+1}}\operatorname{grad}f(y_k) \Bigr)$
6. $γ_{k+1} = \frac{1}{1+β_k}\barγ_{k+1}$

Then the direction from $p_k$ to $p_k+1$ by $d = \operatorname{retr}^{-1}_{p_k}p_{k+1}$ is returned.

# Input

  * `M::`[`AbstractManifold`](@extref `ManifoldsBase.AbstractManifold`)``: a Riemannian manifold $\mathcal M$ (optional)

# Keyword arguments

  * `p=`[`rand`](@extref Base.rand-Tuple{AbstractManifold})`(M)`: a point on the manifold $\mathcal M$to specify the initial value
  * `γ=0.001`
  * `μ=0.9`
  * `shrinkage = k -> 0.8`
  * `inverse_retraction_method=`[`default_inverse_retraction_method`](@extref `ManifoldsBase.default_inverse_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: an inverse retraction $\operatorname{retr}^{-1}$ to use, see [the section on retractions and their inverses](@extref ManifoldsBase :doc:`retractions`)

!!! info
    This function generates a [`ManifoldDefaultsFactory`](@ref) for [`NesterovRule`](@ref). For default values, that depend on the manifold, this factory postpones the construction until the manifold from for example a corresponding [`AbstractManoptSolverState`](@ref) is available.

