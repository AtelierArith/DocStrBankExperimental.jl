```
AMGPreconditioner(;max_levels=10, max_coarse=10)
AMGPreconditioner(matrix;max_levels=10, max_coarse=10)
```

Create the  [`AMGPreconditioner`](@ref) wrapping the Ruge-Stüben AMG preconditioner from [AlgebraicMultigrid.jl](https://github.com/JuliaLinearAlgebra/AlgebraicMultigrid.jl)

!!! warning
    Deprecated in favor of [`RS_AMGPreconditioner`](@ref)

