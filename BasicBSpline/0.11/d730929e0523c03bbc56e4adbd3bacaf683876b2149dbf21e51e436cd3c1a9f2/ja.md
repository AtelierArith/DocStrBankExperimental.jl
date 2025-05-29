```
@knotvector_str -> KnotVector
```

重複するノットの数を指定してノットベクターを構築します。

# 例

```jldoctest
julia> knotvector"11111"
KnotVector([1, 2, 3, 4, 5])

julia> knotvector"123"
KnotVector([1, 2, 2, 3, 3, 3])

julia> knotvector" 2 2 2"
KnotVector([2, 2, 4, 4, 6, 6])

julia> knotvector"     1"
KnotVector([6])
```
