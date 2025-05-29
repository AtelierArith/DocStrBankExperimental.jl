```
permutations(a)
```

インデックス可能なオブジェクト `a` のすべての順列を辞書式順序で生成します。順列の数が非常に大きくなる可能性があるため、この関数はイテレータオブジェクトを返します。すべての順列の配列を取得するには `collect(permutations(a))` を使用してください。定義された長さを持つ `a` のみで機能します。

# 例

```jldoctest
julia> permutations(1:2)
Combinatorics.Permutations{UnitRange{Int64}}(1:2, 2)

julia> collect(permutations(1:2))
2-element Vector{Vector{Int64}}:
 [1, 2]
 [2, 1]

julia> collect(permutations(1:3))
6-element Vector{Vector{Int64}}:
 [1, 2, 3]
 [1, 3, 2]
 [2, 1, 3]
 [2, 3, 1]
 [3, 1, 2]
 [3, 2, 1]
```
