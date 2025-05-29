```
FunctionField(func::F, grid::StructuredGrid{N}, loc; discrete=false, parameters=nothing) where {F,N}
```

Create a `FunctionField` on the given `grid` using the specified function `func`.

## Arguments:

  * `func::F`: The function used to generate the field values.
  * `grid::StructuredGrid{N}`: The structured grid defining the computational domain.
  * `loc`: The nodal location on the grid grid where the function field is defined on.
  * `discrete=false`: A flag indicating whether the field should be discrete. Defaults to `false`.
  * `parameters=nothing`: Additional parameters to be used by the function. Defaults to `nothing`.
