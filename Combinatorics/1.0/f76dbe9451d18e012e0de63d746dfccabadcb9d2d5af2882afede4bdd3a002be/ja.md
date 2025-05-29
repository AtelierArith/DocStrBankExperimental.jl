```
multiset_permutations(a, t)
```

配列 `a` から重複する要素を持つ可能性のあるサイズ `t` のすべての順列を生成します。

# 例

```jldoctest
julia> collect(permutations([1,1,1], 2))
6-element Vector{Vector{Int64}}:
 [1, 1]
 [1, 1]
 [1, 1]
 [1, 1]
 [1, 1]
 [1, 1]

julia> collect(multiset_permutations([1,1,1], 2))
1-element Vector{Vector{Int64}}:
 [1, 1]

julia> collect(multiset_permutations([1,1,2], 3))
3-element Vector{Vector{Int64}}:
 [1, 1, 2]
 [1, 2, 1]
 [2, 1, 1]
```
