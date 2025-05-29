```
remove_joint!(g::BVHGraph, v::Integer, v₊₁::Integer = outneighbors(g, v) != [] ? outneighbors(g, v)[1] : 0)
```

Remove a vertex `v` and adjust the offsets and rotations of the surrounding vertices in such a way  that deviations from their original positions are minimized.

In the case that `v` possesses multiple outneighbors, a neighbor `v₊₁` can be specified that  will be prioritized when adjusting rotations. `v` and `v₊₁` can also be identified by their name.

See also: [`remove_joints!`](@ref), [`optimize_offsets!`](@ref)
