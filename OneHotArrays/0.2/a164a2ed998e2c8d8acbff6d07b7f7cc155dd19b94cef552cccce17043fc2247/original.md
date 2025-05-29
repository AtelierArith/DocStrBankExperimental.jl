```
onehotbatch(xs, labels, [default])
```

Returns a [`OneHotMatrix`](@ref) where `k`th column of the matrix is [`onehot(xs[k], labels)`](@ref onehot). This is a sparse matrix, which stores just a `Vector{UInt32}` containing the indices of the nonzero elements.

If one of the inputs in `xs` is not found in `labels`, that column is `onehot(default, labels)` if `default` is given, else an error.

If `xs` has more dimensions, `N = ndims(xs) > 1`, then the result is an  `AbstractArray{Bool, N+1}` which is one-hot along the first dimension,  i.e. `result[:, k...] == onehot(xs[k...], labels)`.

Note that `xs` can be any iterable, such as a string. And that using a tuple for `labels` will often speed up construction, certainly for less than 32 classes.

# Examples

```jldoctest
julia> oh = onehotbatch("abracadabra", 'a':'e', 'e')
5×11 OneHotMatrix(::Vector{UInt32}) with eltype Bool:
 1  ⋅  ⋅  1  ⋅  1  ⋅  1  ⋅  ⋅  1
 ⋅  1  ⋅  ⋅  ⋅  ⋅  ⋅  ⋅  1  ⋅  ⋅
 ⋅  ⋅  ⋅  ⋅  1  ⋅  ⋅  ⋅  ⋅  ⋅  ⋅
 ⋅  ⋅  ⋅  ⋅  ⋅  ⋅  1  ⋅  ⋅  ⋅  ⋅
 ⋅  ⋅  1  ⋅  ⋅  ⋅  ⋅  ⋅  ⋅  1  ⋅

julia> reshape(1:15, 3, 5) * oh  # this matrix multiplication is done efficiently
3×11 Matrix{Int64}:
 1  4  13  1  7  1  10  1  4  13  1
 2  5  14  2  8  2  11  2  5  14  2
 3  6  15  3  9  3  12  3  6  15  3
```
