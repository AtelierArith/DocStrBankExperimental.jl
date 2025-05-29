```julia
fill!(
    B::GradientRobustMultiPhysics.FEMatrixBlock{Tv, Ti},
    value
)

```

Custom `fill` function for `FEMatrixBlock` (only fills the block, not the complete FEMatrix).
