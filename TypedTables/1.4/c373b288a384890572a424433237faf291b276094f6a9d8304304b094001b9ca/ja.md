```
deleteproperty(object, name::Symbol)
```

指定された`name`を持つプロパティが削除された`object`のコピーを返します。

# 例

```
julia> nt = (a = 1, b = 2.0, c = false)
(a = 1, b = 2.0, c = false)

julia> deleteproperty(nt, :b)
(a = 1, c = false)
```
