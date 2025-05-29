```
path(::AirTable)
```

Accessor function for the API path to the table. This is just the table ID preceded by the [path to the base](@ref `path(::AirBase)`)

```jldoctest
julia> b = AirBase("appphImnhJO8AXmmo");

julia> tab = AirTable("Table 1", b);

julia> path(tab)
"/v0/appphImnhJO8AXmmo/Table 1"
```
