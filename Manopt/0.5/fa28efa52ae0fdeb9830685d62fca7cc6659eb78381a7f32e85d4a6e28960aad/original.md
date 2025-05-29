```
StopWhenGradientNormLess <: StoppingCriterion
```

A stopping criterion based on the current gradient norm.

# Fields

  * `norm`:      a function `(M::AbstractManifold, p, X) -> ℝ` that computes a norm of the gradient `X` in the tangent space at `p` on `M``. For manifolds with components provide`(M::AbstractManifold, p, X, r) -> ℝ`.
  * `threshold`: the threshold to indicate to stop when the distance is below this value
  * `outer_norm`: if `M` is a manifold with components, this can be used to specify the norm, that is used to compute the overall distance based on the element-wise distance.

# Internal fields

  * `last_change` store the last change
  * `at_iteration` store the iteration at which the stop indication happened

# Example

On an [`AbstractPowerManifold`](@extref `ManifoldsBase.AbstractPowerManifold`) like $\mathcal M = \mathcal N^n$ any point $p = (p_1,…,p_n) ∈ \mathcal M$ is a vector of length $n$ with of points $p_i ∈ \mathcal N$. Then, denoting the `outer_norm` by $r$, the norm of a tangent vector like the current gradient $X ∈ \mathcal M$ is given by

```
\lVert X \rVert_{p} = \Bigl( \sum_{k=1}^n \lVert X_k \rVert_{p_k}^r \Bigr)^{\frac{1}{r}},
```

where the sum turns into a maximum for the case $r=∞$. The `outer_norm` has no effect on manifolds that do not consist of components.

If you pass in your individual norm, this can be deactivated on such manifolds by passing `missing` to `outer_norm`.

# Constructor

```
StopWhenGradientNormLess(ε; norm=ManifoldsBase.norm, outer_norm=missing)
```

Create a stopping criterion with threshold `ε` for the gradient, that is, this criterion indicates to stop when [`get_gradient`](@ref) returns a gradient vector of norm less than `ε`, where the norm to use can be specified in the `norm=` keyword.
