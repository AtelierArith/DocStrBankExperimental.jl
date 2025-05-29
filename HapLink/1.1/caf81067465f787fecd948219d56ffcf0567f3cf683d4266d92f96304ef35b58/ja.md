```
sumsliced(A::AbstractArray, dim::Int, pos::Int=1)
```

`A`の`dim`次元において`pos`で参照できるすべての要素を合計します。

# 例

```jldoctest
julia> A = reshape(1:8, 2, 2, 2)
2×2×2 reshape(::UnitRange{Int64}, 2, 2, 2) with eltype Int64:
[:, :, 1] =
 1  3
 2  4

[:, :, 2] =
 5  7
 6  8

julia> sumsliced(A, 2)
14

julia> sumsliced(A, 2, 2)
22
```

Holy, Tim "Multidimensional algorithms and iteration" [https://julialang.org/blog/2016/02/iteration/#filtering*along*a*specified*dimension*exploiting*multiple_indexes](https://julialang.org/blog/2016/02/iteration/#filtering_along_a_specified_dimension_exploiting_multiple_indexes) に強く影響を受けています。
