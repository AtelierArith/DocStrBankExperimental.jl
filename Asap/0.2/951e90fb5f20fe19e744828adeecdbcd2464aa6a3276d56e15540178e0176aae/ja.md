```
FDMload(points::Vector{FDMnode}, i::Int64, force::Vector{<:Real})
FDMload(point::FDMnode, force::Vector{<:Real})
```

FDMノードに加えられる外力: `load = [Px, Py, Pz]`
