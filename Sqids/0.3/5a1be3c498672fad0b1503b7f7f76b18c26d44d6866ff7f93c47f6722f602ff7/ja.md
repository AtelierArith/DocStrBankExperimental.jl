```
encode(config::Sqids.Configuration, numbers::Array{<:Integer})
```

渡された `numbers` を id にエンコードします。

# 例

```julia-repl
julia> encode(Sqids.configure(), [1, 2, 3])
"86Rf07"

```
