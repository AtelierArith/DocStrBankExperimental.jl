```
select!(index::Index, key::AbstractString, value::AbstractString)
select!(index::Index, key::AbstractString, value::AbstractFloat)
select!(index::Index, key::AbstractString, value::AbstractFloat)
```

インデックスのサイズをキーと値のペアに一致するメッセージに縮小します。

# 例

```Julia
Index(filename, "shortName") do index
    select!(index, "shortName", "tp")
    # インデックスは現在、総降水量に関するメッセージのみを持っています
end

Index(filename, "level") do index
    select!(index, "level", 850)
    # インデックスは現在、レベル850のメッセージのみを持っています
end
```
