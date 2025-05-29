```
path(::AirBase)
```

Accessor function for the API path to the base. This is just the base ID preceded by the API version number (only `v0` for now).

```jldoctest
julia> b = AirBase("appphImnhJO8AXmmo");

julia> path(b)
"/v0/appphImnhJO8AXmmo"
```
