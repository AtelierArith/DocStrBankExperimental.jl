```
length(at::AliasTable)
```

`at` が構築された重みの数を取得します。末尾のゼロも含まれます。

# 例

```jldoctest
julia> length(AliasTable([1, 3, 0]))
3
```
