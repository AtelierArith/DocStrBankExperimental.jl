```
getmode(message::AbstractString)
```

`message`のエンコーディングモードを返します。`Numeric()`, `Alphanumeric()`, `Byte()`または`Kanji()`のいずれかです。

# 例

```jldoctest
julia> getmode("HELLO WORLD")
Alphanumeric()
```

```jldoctest
julia> getmode("0123456")
Numeric()
```

```jldoctest
julia> getmode("12αβ")
UTF8()
```

```jldoctest
julia> getmode("茗荷")
Kanji()
```
