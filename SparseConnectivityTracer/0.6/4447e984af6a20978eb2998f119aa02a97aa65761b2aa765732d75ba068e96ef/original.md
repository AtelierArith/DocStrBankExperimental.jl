```
TracerSparsityDetector <: ADTypes.AbstractSparsityDetector
```

Singleton struct for integration with the sparsity detection framework of [ADTypes.jl](https://github.com/SciML/ADTypes.jl).

Computes global sparsity patterns over the entire input domain. For local sparsity patterns at a specific input point, use [`TracerLocalSparsityDetector`](@ref).

# Example

```jldoctest
julia> using SparseConnectivityTracer

julia> detector = TracerSparsityDetector()
TracerSparsityDetector()

julia> jacobian_sparsity(diff, rand(4), detector)
3×4 SparseArrays.SparseMatrixCSC{Bool, Int64} with 6 stored entries:
 1  1  ⋅  ⋅
 ⋅  1  1  ⋅
 ⋅  ⋅  1  1

julia> f(x) = x[1] + x[2]*x[3] + 1/x[4];

julia> hessian_sparsity(f, rand(4), detector)
4×4 SparseArrays.SparseMatrixCSC{Bool, Int64} with 3 stored entries:
 ⋅  ⋅  ⋅  ⋅
 ⋅  ⋅  1  ⋅
 ⋅  1  ⋅  ⋅
 ⋅  ⋅  ⋅  1
```
