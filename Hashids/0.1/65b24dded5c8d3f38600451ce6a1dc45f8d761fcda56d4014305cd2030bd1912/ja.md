```
decode(config::Hashids.Configuration, hashid::AbstractString)
```

渡された `hashid` から数値のリストを復元します。

# 例

```julia-repl
julia> decode(Hashids.configure(), "o2fXhV")
3-element Array{Int64,1}:
 1
 2
 3

```
