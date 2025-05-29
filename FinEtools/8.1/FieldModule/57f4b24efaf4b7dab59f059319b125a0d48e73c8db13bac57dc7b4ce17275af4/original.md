```
AbstractField
```

Abstract field.

Expected  attributes:

  * `values::Array{T,2}`: Array of degree of freedom parameters,  indexed by entity number
  * `dofnums::Array{IT,2}`: Array of degree of freedom numbers, indexed by entity number
  * `kind::Matrix{Int8}`: Array of Boolean flags, indexed by entity number
  * `ranges::Dict(Int8, UnitRange{IT})`: Dictionary of ranges for the degrees of freedom.

See also: [`@add_Field_fields()`](@ref) .
