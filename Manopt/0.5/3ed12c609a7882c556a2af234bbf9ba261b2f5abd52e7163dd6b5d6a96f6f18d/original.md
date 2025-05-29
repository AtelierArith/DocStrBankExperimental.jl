```
CyclicProximalPointState <: AbstractManoptSolverState
```

stores options for the [`cyclic_proximal_point`](@ref) algorithm. These are the

# Fields

  * `p::P`: a point on the manifold $\mathcal M$storing the current iterate
  * `stop::StoppingCriterion`: a functor indicating that the stopping criterion is fulfilled
  * `λ`:         a function for the values of $λ_k$ per iteration(cycle $k$
  * `oder_type`: whether to use a randomly permuted sequence (`:FixedRandomOrder`), a per cycle permuted sequence (`:RandomOrder`) or the default linear one.

# Constructor

```
CyclicProximalPointState(M::AbstractManifold; kwargs...)
```

Generate the options

## Input

  * `M::`[`AbstractManifold`](@extref `ManifoldsBase.AbstractManifold`)``: a Riemannian manifold $\mathcal M$

# Keyword arguments

  * `evaluation_order=:LinearOrder`: soecify the `order_type`
  * `λ=i -> 1.0 / i` a function to compute the $λ_k, k ∈ \mathcal N$,
  * `p=`[`rand`](@extref Base.rand-Tuple{AbstractManifold})`(M)`: a point on the manifold $\mathcal M$to specify the initial value
  * `stopping_criterion=`[`StopAfterIteration`](@ref)`(2000)`: a functor indicating that the stopping criterion is fulfilled

# See also

[`cyclic_proximal_point`](@ref)
