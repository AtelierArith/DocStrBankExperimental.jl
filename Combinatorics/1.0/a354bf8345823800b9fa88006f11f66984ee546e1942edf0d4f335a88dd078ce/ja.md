```
nthperm(a, k)
```

ベクトル `a` の `k` 番目の辞書順の順列を計算します。

# 例

```jldoctest
julia> collect(permutations([1,2]))
2-element Vector{Vector{Int64}}:
 [1, 2]
 [2, 1]

julia> nthperm([1,2], 1)
2-element Vector{Int64}:
 1
 2

julia> nthperm([1,2], 2)
2-element Vector{Int64}:
 2
 1

julia> nthperm([1,2], 3)
ERROR: ArgumentError: permutation k must satisfy 0 < k ≤ 2, got 3
[...]
```
