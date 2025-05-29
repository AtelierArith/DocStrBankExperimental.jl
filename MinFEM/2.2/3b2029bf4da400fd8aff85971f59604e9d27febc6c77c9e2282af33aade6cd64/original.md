```julia
mutable struct Domain <: MinFEM.Region
```

Type holding the name and the set of element indices for one particular physical domain.

# Fields

  * `Name::String`: Unique physical name
  * `Nodes::Set{Int64}`: List of node indices
  * `Elements::Set{Int64}`: List of element indices
