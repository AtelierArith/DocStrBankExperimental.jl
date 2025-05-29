```julia
adjacent_tree(_rng, trajectory, z, i, depth, is_forward)

```

Traverse the tree of given `depth` adjacent to point `z` in `trajectory`. `is_forward` specifies the direction, `rng` is used for random numbers in [`combine_proposals`](@ref). `i` is an integer position relative to the initial node (`0`). The *first value* is either

1. an `InvalidTree`, indicating the first divergent node or turning subtree that was

encounteted and invalidated this tree.

2. a tuple of `(ζ, ω, τ, z′, i′), with

      * `ζ`: the proposal from the tree.
      * `ω`: the log weight of the subtree that corresponds to the proposal
      * `τ`: turn statistics
      * `z′`: the last node of the tree
      * `i′`: the position of the last node relative to the initial node.

The *second value* is always the visited node statistic.

# Examples

```julia

```
