```
@derived_dimension(name, dims, autodocs=false)
```

Creates type aliases to allow dispatch on [`Unitful.Quantity`](@ref), [`Unitful.Level`](@ref), and [`Unitful.Units`](@ref) objects of a derived dimension, like area, which is just length squared. The type aliases are not exported. If `autodocs == true`, docstrings will be automatically generated for these aliases.

!!! compat "Unitful 1.10"
    The `autodocs` argument requires Unitful 1.10 or later.


`dims` is a [`Unitful.Dimensions`](@ref) object.

Returns `nothing`.

Usage examples:

  * `@derived_dimension Area 𝐋^2` gives `Area` and `AreaUnit` type aliases
  * `@derived_dimension Speed 𝐋/𝐓` gives `Speed` and `SpeedUnit` type aliases
