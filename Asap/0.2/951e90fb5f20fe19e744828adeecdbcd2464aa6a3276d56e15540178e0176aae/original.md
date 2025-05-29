```
FDMload(points::Vector{FDMnode}, i::Int64, force::Vector{<:Real})
FDMload(point::FDMnode, force::Vector{<:Real})
```

An external force applied to a FDM node: `load = [Px, Py, Pz]`
