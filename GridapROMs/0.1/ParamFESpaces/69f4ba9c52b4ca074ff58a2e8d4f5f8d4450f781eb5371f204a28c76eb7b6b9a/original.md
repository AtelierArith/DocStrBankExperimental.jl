```
parameterize(a::SparseMatrixAssembler,r::AbstractRealization) -> SparseMatrixAssembler
```

Returns an assembler that also stores the parametric length of `r`. This function is to be used to assemble parametric residuals and Jacobians. The assembly routines follow the same pipeline as in [`Gridap`](@ref)
