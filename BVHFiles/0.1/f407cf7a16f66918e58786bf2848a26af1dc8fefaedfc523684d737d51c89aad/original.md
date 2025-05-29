```
optimize_offsets!(g::BVHGraph)
```

For each edge calculate the average norm of the global positions between its source  and destination, then adjust the offset vector accordingly.

After removing vertices this function can reduce the deviations of the vertices from  their original global positions since the new offsets are usually biased.

# Examples

```julia
julia> g = load("Test.bvh") |>
           global_positions! |>
           remove_joint!(7) |>
           remove_joint!(13) |>
           remove_joints!("J_L_Bale", "J_R_Bale", "J_L4", "J_L3", "J_L1", "J_T12", "J_T10", "J_T9", "J_T8", "J_T6", "J_T5", "J_T4", "J_T3", "J_T2") |>
           optimize_offsets!
BVHGraph
Name: Test.bvh
[...]
```

See also: [`total_squared_errors`](@ref)
