```
haskey(collection, key) -> Bool
```

コレクションが指定された `key` に対してマッピングを持っているかどうかを判断します。

# 例

```jldoctest
julia> D = SwissDict('a'=>2, 'b'=>3)
SwissDict{Char, Int64} with 2 entries:
  'a' => 2
  'b' => 3

julia> haskey(D, 'a')
true

julia> haskey(D, 'c')
false
```
