```
StopWhenGradientChangeLess <: StoppingCriterion
```

A stopping criterion based on the change of the gradient.

# Fields

  * `at_iteration::Int`: an integer indicating at which the stopping criterion last indicted to stop, which might also be before the solver started (`0`). Any negative value indicates that this was not yet the case;
  * `last_change::Real`: the last change recorded in this stopping criterion
  * `vector_transport_method::AbstractVectorTransportMethodP`: a vector transport $\mathcal T_{⋅←⋅}$ to use, see [the section on vector transports](@extref ManifoldsBase :doc:`vector_transports`)
  * `storage::StoreStateAction`: a storage to access the previous iterate
  * `threshold`: the threshold for the change to check (run under to stop)
  * `outer_norm`: if `M` is a manifold with components, this can be used to specify the norm, that is used to compute the overall distance based on the element-wise distance. You can deactivate this, but setting this value to `missing`.

# Example

On an [`AbstractPowerManifold`](@extref `ManifoldsBase.AbstractPowerManifold`) like $\mathcal M = \mathcal N^n$ any point $p = (p_1,…,p_n) ∈ \mathcal M$ is a vector of length $n$ with of points $p_i ∈ \mathcal N$. Then, denoting the `outer_norm` by $r$, the norm of the difference of tangent vectors like the last and current gradien $X,Y ∈ \mathcal M$ is given by

```
\lVert X-Y \rVert_{p} = \Bigl( \sum_{k=1}^n \lVert X_k-Y_k \rVert_{p_k}^r \Bigr)^{\frac{1}{r}},
```

where the sum turns into a maximum for the case $r=∞$. The `outer_norm` has no effect on manifols, that do not consist of components.

# Constructor

```
StopWhenGradientChangeLess(
    M::AbstractManifold,
    ε::Float64;
    storage::StoreStateAction=StoreStateAction([:Iterate]),
    vector_transport_method::IRT=default_vector_transport_method(M),
    outer_norm::N=missing
)
```

Create a stopping criterion with threshold `ε` for the change gradient, that is, this criterion indicates to stop when [`get_gradient`](@ref) is in (norm of) its change less than `ε`, where `vector_transport_method` denotes the vector transport $\mathcal T$ used.
