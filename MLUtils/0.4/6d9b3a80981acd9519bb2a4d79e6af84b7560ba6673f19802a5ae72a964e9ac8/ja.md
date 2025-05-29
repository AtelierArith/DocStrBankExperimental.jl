```
unsqueeze(x; dims)
```

`x`を`x`より1次元高い配列に再形成し、`dims`は`x`が拡張される次元を示します。`dims`は1から`ndims(x)+1`の間の整数であることができます。

関連項目としては[`flatten`](@ref)、`stack`があります。

# 例

```jldoctest
julia> unsqueeze([1 2; 3 4], dims=2)
2×1×2 Array{Int64, 3}:
[:, :, 1] =
 1
 3

[:, :, 2] =
 2
 4


julia> xs = [[1, 2], [3, 4], [5, 6]]
3-element Vector{Vector{Int64}}:
 [1, 2]
 [3, 4]
 [5, 6]

julia> unsqueeze(xs, dims=1)
1×3 Matrix{Vector{Int64}}:
 [1, 2]  [3, 4]  [5, 6]
```
