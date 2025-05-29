```
set_xy!(h::HasseDiagram, xy::Dict{Int,Vector{T}}) where {T}
```

Give the Hasse diagram an embedding from a dictionary. If a vertex  does not appear in `xy`, then its position is unchanged. 
