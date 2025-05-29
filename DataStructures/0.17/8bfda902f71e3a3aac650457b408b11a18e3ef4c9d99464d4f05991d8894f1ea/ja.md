```
haskey(collection, key) -> Bool
```

指定された `key` に対してコレクションにマッピングがあるかどうかを判断します。

# 例

```jldoctest
julia> D = RobinDict('a'=>2, 'b'=>3)
RobinDict{Char,Int64} with 2 entries:
  'a' => 2
  'b' => 3

julia> haskey(D, 'a')
true

julia> haskey(D, 'c')
false
```
