```
getmode(message::AbstractString)
```

`message`のエンコーディングモードを返します。`Numeric()`, `Alphanumeric()` または `Byte()` のいずれかです。

# 例

```jldoctest
julia> getmode("HELLO WORLD")
Alphanumeric()
```
