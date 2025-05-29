```
sparse_hessian(expression::Node, variable_order::AbstractVector{<:Node})
```

Compute a sparse symbolic Hessian. Returns a sparse matrix of symbolic expressions.  Can be used in combination with `make_function` to generate an executable that  will return a sparse matrix or take one as an in-place argument.

# Example

```julia
julia> @variables x y

julia> a = sparse_hessian(x*y,[x,y])
2×2 SparseArrays.SparseMatrixCSC{FastDifferentiation.Node, Int64} with 2 stored entries:
 ⋅  1
 1  ⋅

julia> f1 = make_function(a,[x,y])
...

julia> f1([1.0,2.0])
2×2 SparseArrays.SparseMatrixCSC{Float64, Int64} with 2 stored entries:
  ⋅   1.0
 1.0   ⋅

julia> tmp = similar(a,Float64)
2×2 SparseArrays.SparseMatrixCSC{Float64, Int64} with 2 stored entries:
  ⋅            4.24399e-314
 4.24399e-314   ⋅

julia> f2 = make_function(a,[x,y],in_place=true)
...

julia> f2(tmp, [1.0,2.0])
2×2 SparseArrays.SparseMatrixCSC{Float64, Int64} with 2 stored entries:
  ⋅   1.0
 1.0   ⋅

julia> tmp
2×2 SparseArrays.SparseMatrixCSC{Float64, Int64} with 2 stored entries:
  ⋅   1.0
 1.0   ⋅

```
