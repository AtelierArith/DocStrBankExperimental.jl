```
resolve(identstr::AbstractString, parameters::Union{SmallDict{String, Any}, Nothing}=nothing;
        resolvetype::Bool=true, stack::Vector{DataCollection}=STACK)
```

`identstr` と `parameters` で指定された識別子を、データ `stack` の各レイヤーに対して順番に解決しようとします。
