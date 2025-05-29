```
encode(config::Hashids.Configuration, values::Array{<:Integer})  
encode(config::Hashids.Configuration, values::Integer...)
```

渡された `values` をハッシュにエンコードします。

# 例

```julia-repl
julia> encode(Hashids.configure(), 1, 2, 3)
"o2fXhV"

julia> encode(Hashids.configure(), [1, 2, 3])
"o2fXhV"

```
