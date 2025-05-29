```
interacting_pairs(model, r, method; scheduler = abmscheduler(model)) → piter
```

Return an iterator that yields **unique pairs** of agents `(a, b)` that are close neighbors to each other, within some interaction radius `r`.

This function is usefully combined with `model_step!`, when one wants to perform some pairwise interaction across all pairs of close agents once (and does not want to trigger the event twice, both with `a` and with `b`, which would be unavoidable when using `agent_step!`). This means, that if a pair `(a, b)` exists, the pair `(b, a)` is not included in the iterator!

Use `piter.pairs` to get a vector of pair IDs from the iterator.

The argument `method` provides three pairing scenarios

  * `:all`: return every pair of agents that are within radius `r` of each other, not only the nearest ones.
  * `:nearest`: agents are only paired with their true nearest neighbor (existing within radius `r`). Each agent can only belong to one pair, therefore if two agents share the same nearest neighbor only one of them (sorted by distance, then by next id in `scheduler`) will be paired.
  * `:types`: For mixed agent models only. Return every pair of agents within radius `r` (similar to `:all`), only capturing pairs of differing types. For example, a model of `Union{Sheep,Wolf}` will only return pairs of `(Sheep, Wolf)`. In the case of multiple agent types, e.g. `Union{Sheep, Wolf, Grass}`, skipping pairings that involve `Grass`, can be achieved by a [`scheduler`](@ref Schedulers) that doesn't schedule `Grass` types, i.e.: `scheduler(model) = (a.id for a in allagents(model) if !(a isa Grass))`.

The following keywords can be used:

  * `scheduler = abmscheduler(model)`, which schedulers the agents during iteration for finding pairs. Especially in the `:nearest` case, this is important, as different sequencing for the agents may give different results (if `b` is the nearest agent for `a`, but `a` is not the nearest agent for `b`, whether you get the pair `(a, b)` or not depends on whether `a` was scheduler first or not).
  * `search = :exact` decides how to find nearby IDs in the `:all, :types` cases.  Must be `:exact` or `:approximate`.

Example usage in [Bacterial Growth](https://juliadynamics.github.io/AgentsExampleZoo.jl/dev/examples/growing_bacteria/) model.

!!! note "Better performance with CellListMap.jl"
    Notice that in most applications that [`interacting_pairs`](@ref) is useful, there is significant (10x-100x) performance gain to be made by integrating with CellListMap.jl. Checkout the [Integrating Agents.jl with CellListMap.jl](@ref) integration example for how to do this.

