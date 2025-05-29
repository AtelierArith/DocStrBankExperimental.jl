```
StopWhenChangeLess <: StoppingCriterion
```

stores a threshold when to stop looking at the norm of the change of the optimization variable from within a [`AbstractManoptSolverState`](@ref) `s`. That ism by accessing `get_iterate(s)` and comparing successive iterates. For the storage a [`StoreStateAction`](@ref) is used.

# Fields

  * `at_iteration::Int`: an integer indicating at which the stopping criterion last indicted to stop, which might also be before the solver started (`0`). Any negative value indicates that this was not yet the case;
  * `last_change::Real`: the last change recorded in this stopping criterion
  * `inverse_retraction_method::AbstractInverseRetractionMethod`: an inverse retraction $\operatorname{retr}^{-1}$ to use, see [the section on retractions and their inverses](@extref ManifoldsBase :doc:`retractions`)
  * `storage::StoreStateAction`: a storage to access the previous iterate
  * `at_iteration::Int`: indicate at which iteration this stopping criterion was last active.
  * `inverse_retraction`: An [`AbstractInverseRetractionMethod`](@extref `ManifoldsBase.AbstractInverseRetractionMethod`) that can be passed to approximate the distance by this inverse retraction and a norm on the tangent space. This can be used if neither the distance nor the logarithmic map are availannle on `M`.
  * `last_change`: store the last change
  * `storage`: A [`StoreStateAction`](@ref) to access the previous iterate.
  * `threshold`: the threshold for the change to check (run under to stop)
  * `outer_norm`: if `M` is a manifold with components, this can be used to specify the norm, that is used to compute the overall distance based on the element-wise distance. You can deactivate this, but setting this value to `missing`.

# Example

On an [`AbstractPowerManifold`](@extref `ManifoldsBase.AbstractPowerManifold`) like $\mathcal M = \mathcal N^n$ any point $p = (p_1,…,p_n) ∈ \mathcal M$ is a vector of length $n$ with of points $p_i ∈ \mathcal N$. Then, denoting the `outer_norm` by $r$, the distance of two points $p,q ∈ \mathcal M$ is given by

```
\mathrm{d}(p,q) = \Bigl( \sum_{k=1}^n \mathrm{d}(p_k,q_k)^r \Bigr)^{\frac{1}{r}},
```

where the sum turns into a maximum for the case $r=∞$. The `outer_norm` has no effect on manifolds that do not consist of components.

If the manifold does not have components, the outer norm is ignored.

# Constructor

```
StopWhenChangeLess(
    M::AbstractManifold,
    threshold::Float64;
    storage::StoreStateAction=StoreStateAction([:Iterate]),
    inverse_retraction_method::IRT=default_inverse_retraction_method(M)
    outer_norm::Union{Missing,Real}=missing
)
```

initialize the stopping criterion to a threshold `ε` using the [`StoreStateAction`](@ref) `a`, which is initialized to just store `:Iterate` by default. You can also provide an inverse*retraction*method for the `distance` or a manifold to use its default inverse retraction.
