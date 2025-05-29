```
FDMelement(points::Vector{FDMnode}, iStart::Int64, iEnd::Int64, q::Real, id = :element)
FDMelement(points::Vector{FDMnode}, indices::Vector{Int64}, q::Real, id = :element)
FDMelement(pointStart::FDMnode, pointEnd::FDMnode, q::Real, id = :element)
```

An element in a Force Density Method network that connects two nodes with force density `q` and an optional identifier `id::Symbol`
