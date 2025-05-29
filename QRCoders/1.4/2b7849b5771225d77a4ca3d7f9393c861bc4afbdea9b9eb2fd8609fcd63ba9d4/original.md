```
getmode(message::AbstractString)
```

Return the encoding mode of `message`, either `Numeric()`, `Alphanumeric()`,  `Byte()` or Kanji().

# Examples

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
