```
remove_joints!(g::BVHGraph, names::AbstractString...)
```

Remove every vertex in `names` and adjust the offsets and rotations of the surrounding vertices  in such a way that deviations from their original positions are minimized.

See also: [`remove_joint!`](@ref), [`optimize_offsets!`](@ref)
