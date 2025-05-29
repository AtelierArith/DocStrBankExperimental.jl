```
StackView(slices...; [dims])
StackView(slices, [dims])
StackView{T}(args...; kwargs...)
```

Stack/concatenate a list of arrays `slices` along dimension `dims` without copying the data.

If not specified, `dims` is defined as `ndims(first(slices))+1`, i.e., a new dimension in the tail. This works better for normal Julia arrays when their memory layout is column-major.

# Example

`StackView` works very similar to `cat` and its `vcat`/`hcat`/`hvcat` variants.

```jldoctest; setup=:(using StackViews)
julia> A = reshape(collect(1:6), 2, 3);

julia> B = reshape(collect(7:12), 2, 3);

julia> StackView(A, B, dims=3) # mostly equivalent to `cat(A, B, dims=3)`
2×3×2 StackView{Int64, 3, 3, Tuple{Matrix{Int64}, Matrix{Int64}}}:
[:, :, 1] =
 1  3  5
 2  4  6

[:, :, 2] =
 7   9  11
 8  10  12
```

The difference comes to when `dim <= ndims(first(slices))`, which is `dim <= 2` for this example. `StackView` always creats new dimension while `cat`s do not.

```jldoctest; setup=:(using StackViews; A = reshape(collect(1:6), 2, 3); B = reshape(collect(7:12), 2, 3);)
julia> StackView(A, B, dims=1) # `cat(A, B, dims=1)` outputs 4×3 Matrix
2×2×3 StackView{Int64, 3, 1, Tuple{Matrix{Int64}, Matrix{Int64}}}:
[:, :, 1] =
 1  2
 7  8

[:, :, 2] =
 3   4
 9  10

[:, :, 3] =
  5   6
 11  12

julia> StackView(A, B, dims=2) # `cat(A, B, dims=2)` outputs 2×6 Matrix
2×2×3 StackView{Int64, 3, 2, Tuple{Matrix{Int64}, Matrix{Int64}}}:
[:, :, 1] =
 1  7
 2  8

[:, :, 2] =
 3   9
 4  10

[:, :, 3] =
 5  11
 6  12
```

!!! tip
    For type-stability, you can pass `Val` as dim, e.g., `StackView(slices, Val(3))`.

