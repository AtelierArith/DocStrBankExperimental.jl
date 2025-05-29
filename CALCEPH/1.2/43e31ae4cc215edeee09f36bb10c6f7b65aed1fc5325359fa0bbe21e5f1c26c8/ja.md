```
naifId
```

NAIF識別番号

例:

```jldoctest
julia> using CALCEPH

julia> naifId.id[:sun]
10

julia> naifId.id[:mars]
499

julia> naifId.names[0]
Set(Symbol[:ssb, :solar_system_barycenter])

```
