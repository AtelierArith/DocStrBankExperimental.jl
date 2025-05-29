```julia
mutable struct Boundary <: MinFEM.Region
```

Structure holding the name and sets of node and edge indices for one particular physical boundary.

# Fields

  * `Name::String`: Unique physical name
  * `Nodes::Set{Int64}`: List of node indices
  * `Elements::Set{Int64}`: List of element indices
