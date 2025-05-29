```
set_data_dimension!(domain::Domain, dim::NamedDimension [, coordinates], ; allow_exists=false)
```

Define a Domain data dimension as a [`NamedDimension`](@ref), optionally attaching a Vector of coordinate names.

Variables may then specify data dimensions as a list of names using the `:data_dims` Variable Attribute.
