```julia
fill!(B::ExtendableFEMBase.FEMatrixBlock{Tv, Ti}, value)

```

Custom `fill` function for `FEMatrixBlock` (only fills the already present nzval in the block, not the complete FEMatrix).
