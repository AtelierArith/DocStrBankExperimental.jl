```
decode(config::Sqids.Configuration, id::AbstractString)
```

渡された `id` から数値のリストを復元します。

# 例

```julia-repl
julia> decode(Sqids.configure(), "86Rf07")
3-element Array{Int64,1}:
 1
 2
 3

```
