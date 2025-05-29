`Param{T}` is a data type representing a general tight-binding parameter, which can span multiple bonds.

# Attributes

  * `value        ::  Vector{ Float64 }`: the strength of the parameter (or even the full history of it if its changed).
  * `unitBonds    ::  Vector{ Bond{T} }`: All the bonds this parameter lives on. These bonds are supposed to have "unit" strength, and ultimately get scaled by the `value` when making the `UnitCell`.
  * `label        ::  String`: some string label to mark the parameter.
  * `dist         ::  Float64`: the distance of the bonds the parameter lives on.

Initialize this structure using 

```julia
Param( value::Float64 )
Param( value::Float64 , rank::Int64 )
```
