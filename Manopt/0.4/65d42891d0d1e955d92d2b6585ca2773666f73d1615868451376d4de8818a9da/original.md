```
CyclicProximalPointState <: AbstractManoptSolverState
```

stores options for the [`cyclic_proximal_point`](@ref) algorithm. These are the

# Fields

  * `p`:                  the current iterate
  * `stopping_criterion`:  a [`StoppingCriterion`](@ref)
  * `λ`:                  (@(i) -> 1/i) a function for the values of $λ_k$ per iteration(cycle $ì$
  * `oder_type`:          (`:LinearOrder`) whether to use a randomly permuted sequence (`:FixedRandomOrder`), a per cycle permuted sequence (`:RandomOrder`) or the default linear one.

# Constructor

```
CyclicProximalPointState(M, p)
```

Generate the options with the following keyword arguments

  * `stopping_criterion`: (`StopAfterIteration(2000)`) a [`StoppingCriterion`](@ref).
  * `λ`:                  ( `i -> 1.0 / i`) a function to compute the $λ_k, k ∈ \mathbb N$,
  * `evaluation_order`:   (`:LinearOrder`) a Symbol indicating the order the proximal maps are applied.

# See also

[`cyclic_proximal_point`](@ref)
