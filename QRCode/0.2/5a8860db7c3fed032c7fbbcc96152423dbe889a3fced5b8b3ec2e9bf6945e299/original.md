```
getmode(message::AbstractString)
```

Return the encoding mode of `message`, either `Numeric()`, `Alphanumeric()` or `Byte()`.

# Examples

```jldoctest
julia> getmode("HELLO WORLD")
Alphanumeric()
```
