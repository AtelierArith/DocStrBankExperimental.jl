```
AMGPreconditioner(;max_levels=10, max_coarse=10)
AMGPreconditioner(matrix;max_levels=10, max_coarse=10)
```

[`AMGPreconditioner`](@ref) を作成し、[AlgebraicMultigrid.jl](https://github.com/JuliaLinearAlgebra/AlgebraicMultigrid.jl) の Ruge-Stüben AMG 前処理器をラップします。

!!! warning
    [`RS_AMGPreconditioner`](@ref) に代わって非推奨です。

