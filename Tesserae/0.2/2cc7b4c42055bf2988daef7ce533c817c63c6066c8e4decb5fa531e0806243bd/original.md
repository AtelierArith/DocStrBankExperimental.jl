```
SpArray{T}(undef, dims...)
```

`SpArray` is a sparse array which has blockwise sparsity pattern. In `SpArray`, it is not allowed to freely change the value like built-in `Array`. For example, trying to `setindex!` doesn't change anything without any errors as

```jldoctest sparray
julia> A = SpArray{Float64}(undef, 5, 5)
5×5 SpArray{Float64, 2}:
 ⋅  ⋅  ⋅  ⋅  ⋅
 ⋅  ⋅  ⋅  ⋅  ⋅
 ⋅  ⋅  ⋅  ⋅  ⋅
 ⋅  ⋅  ⋅  ⋅  ⋅
 ⋅  ⋅  ⋅  ⋅  ⋅

julia> A[1,1]
0.0

julia> A[1,1] = 2 # no error
2

julia> A[1,1] # still zero
0.0
```

This is because the block where index `(1,1)` is located is not activated yet. To activate the block, update sparsity pattern by `update_block_sparsity!(A, spy)` where `spy` must have `Tesserae.blocksize(A)`.

```jldoctest sparray
julia> spy = trues(Tesserae.blocksize(A))
1×1 BitMatrix:
 1

julia> update_block_sparsity!(A, spy) # returned value indicates the number of allocated elements in `A`.
64

julia> A .= 0;

julia> A[1,1] = 2
2

julia> A
5×5 SpArray{Float64, 2}:
 2.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0
```
