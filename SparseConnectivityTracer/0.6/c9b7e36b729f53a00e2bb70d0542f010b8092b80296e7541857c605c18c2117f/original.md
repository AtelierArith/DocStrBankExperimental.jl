```
TracerLocalSparsityDetector <: ADTypes.AbstractSparsityDetector
```

Singleton struct for integration with the sparsity detection framework of [ADTypes.jl](https://github.com/SciML/ADTypes.jl).

Computes local sparsity patterns at an input point `x`. For global sparsity patterns, use [`TracerSparsityDetector`](@ref).

# Example

Local sparsity patterns are less convervative than global patterns and need to be recomputed for each input `x`:

```jldoctest
julia> using SparseConnectivityTracer

julia> detector = TracerLocalSparsityDetector()
TracerLocalSparsityDetector()

julia> f(x) = x[1] * x[2]; # J_f = [x[2], x[1]]

julia> jacobian_sparsity(f, [1, 0], detector)
1×2 SparseArrays.SparseMatrixCSC{Bool, Int64} with 1 stored entry:
 ⋅  1

julia> jacobian_sparsity(f, [0, 1], detector)
1×2 SparseArrays.SparseMatrixCSC{Bool, Int64} with 1 stored entry:
 1  ⋅

julia> jacobian_sparsity(f, [0, 0], detector)
1×2 SparseArrays.SparseMatrixCSC{Bool, Int64} with 0 stored entries:
 ⋅  ⋅

julia> jacobian_sparsity(f, [1, 1], detector)
1×2 SparseArrays.SparseMatrixCSC{Bool, Int64} with 2 stored entries:
 1  1
```

`TracerLocalSparsityDetector` can compute sparsity patterns of functions that contain comparisons and `ifelse` statements:

```jldoctest
julia> f(x) = x[1] > x[2] ? x[1:3] : x[2:4];

julia> jacobian_sparsity(f, [1, 2, 3, 4], TracerLocalSparsityDetector())
3×4 SparseArrays.SparseMatrixCSC{Bool, Int64} with 3 stored entries:
 ⋅  1  ⋅  ⋅
 ⋅  ⋅  1  ⋅
 ⋅  ⋅  ⋅  1

julia> jacobian_sparsity(f, [2, 1, 3, 4], TracerLocalSparsityDetector())
3×4 SparseArrays.SparseMatrixCSC{Bool, Int64} with 3 stored entries:
 1  ⋅  ⋅  ⋅
 ⋅  1  ⋅  ⋅
 ⋅  ⋅  1  ⋅
```

```jldoctest
julia> f(x) = x[1] + max(x[2], x[3]) * x[3] + 1/x[4];

julia> hessian_sparsity(f, [1.0, 2.0, 3.0, 4.0], TracerLocalSparsityDetector())
4×4 SparseArrays.SparseMatrixCSC{Bool, Int64} with 2 stored entries:
 ⋅  ⋅  ⋅  ⋅
 ⋅  ⋅  ⋅  ⋅
 ⋅  ⋅  1  ⋅
 ⋅  ⋅  ⋅  1
```
