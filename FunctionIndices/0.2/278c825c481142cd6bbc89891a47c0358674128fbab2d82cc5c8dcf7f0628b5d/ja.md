```
not(x)
```

与给定的 `x` 创建一个 `NotIndex`，它类似于 [`InvertedIndices`](https://github.com/JuliaData/InvertedIndices.jl) 的 `Not`。在大多数情况下，`not` 的速度比 `Not` 快得多。有关更多详细信息，请参见 [性能比较](@ref performance)。

# `not` 和 `Not` 之间的主要区别

对于 `CartesianIndex`，`A[not(CartesianIndex(i, j,..., n))]` 等价于 `A[not(i), not(j), ..., not(n)]`，并将返回具有相同维度的数组，而 `A[Not(CartesianIndex(i, j,..., n))]` 将把 `CartesianIndex` 转换为线性索引并返回一个向量：

```jldoctest
julia> A = reshape(1:12, 3, 4)
3×4 reshape(::UnitRange{Int64}, 3, 4) with eltype Int64:
 0  3  6   9
 1  4  7  10
 2  5  8  11

julia> A[not(CartesianIndex(1, 2))] # 等价于 A[not(1), not(2)]
2×3 Matrix{Int64}:
 1  7  10
 2  8  11

julia> A[Not(CartesianIndex(1, 2))] # 等价于 A[Not(3)]
11-element Vector{Int64}:
  0
  1
  2
  4
  5
  ⋮
  8
  9
 10
 11
```

此外，对于像 `A[4, 5]` 这样的越界索引，`A[not(4), not(5)]` 等价于 `A[:, :]`，因为有效索引总是不等于给定值，而 `A[Not[4], Not(5)]` 会导致错误。
