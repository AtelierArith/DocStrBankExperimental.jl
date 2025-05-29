```
internal_size(Space::Type{<:AbstractSpace}, mesh::AbstractMesh; [subdomain=""] [space=:cell]) -> NTuple{ndims, Int}
```

Array size to use for model Variables.

All `AbstractMesh` concrete subtypes (UnstructuredVectorGrid, CartesianLinearGrid, ...) should implement this method.

# Optional Keyword Arguments

  * `subdomain::String=""`: a named subdomain
