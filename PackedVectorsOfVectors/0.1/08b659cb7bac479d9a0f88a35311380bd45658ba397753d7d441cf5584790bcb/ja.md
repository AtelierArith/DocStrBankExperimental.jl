```
packed_indices(n) -> pv::PackedVectorOfVectors
```

`k`番目のネストされたベクターの長さが`nth(n,k)`であり、`pv[k][i]`は`k`番目のネストされたベクターの`i`番目の要素のフラット化されたベクターにおけるインデックスであるような、ベクターのベクターのパック。

# 例

```jldoctest
julia> packed_indices([2,3])
2-element pack(::Vector{Vector{Int64}}):
 1:2
 3:5
```
