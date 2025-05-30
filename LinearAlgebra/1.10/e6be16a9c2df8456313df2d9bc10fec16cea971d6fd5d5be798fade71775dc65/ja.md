```
diagind(M, k::Integer=0)
```

行列 `M` の `k` 番目の対角線のインデックスを与える `AbstractRange`。

関連項目: [`diag`](@ref), [`diagm`](@ref), [`Diagonal`](@ref)。

# 例

```jldoctest
julia> A = [1 2 3; 4 5 6; 7 8 9]
3×3 Matrix{Int64}:
 1  2  3
 4  5  6
 7  8  9

julia> diagind(A,-1)
2:4:6
```
