```
@gen(X)(m, s, a)
@gen(X)(m, s, a, rng::AbstractRNG)
```

Call the generative model for a (PO)MDP `m`; Sample values from several nodes in the dynamic decision network. X is one or more symbols indicating which nodes to output.

Solvers and simulators should call this rather than the `gen` function. Problem writers should implement a method of the `transition` or `gen` function instead of altering `@gen`.

# Arguments

  * `m`: an `MDP` or `POMDP` model
  * `s`: the current state
  * `a`: the action
  * `rng` (optional): a random number generator (Typically a `MersenneTwister`)

# Return

If `X`, is a symbol, return a value sample from the corresponding node. If `X` is several symbols, return a `Tuple` of values sampled from the specified nodes.

# Examples

Let `m` be an `MDP` or `POMDP`, `s` be a state of `m`, `a` be an action of `m`, and `rng` be an `AbstractRNG`.

  * `@gen(:sp, :r)(m, s, a)` returns a `Tuple` containing the next state and reward.
  * `@gen(:sp, :o, :r)(m, s, a, rng)` returns a `Tuple` containing the next state, observation, and reward.
  * `@gen(:sp)(m, s, a, rng)` returns the next state.
