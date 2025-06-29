```
@unit(symb,abbr,name,equals,tf,autodocs=false)
```

Define a unit. Rather than specifying a dimension like in [`@refunit`](@ref), `equals` should be a [`Unitful.Quantity`](@ref) equal to one of the unit being defined. If `tf == true`, symbols will be made for each power-of-ten prefix. If `autodocs == true`, autogenerated docstrings for SI-prefixed units will be added. This option has no effect when `tf == false`.

!!! compat "Unitful 1.10"
    Documenting the resulting unit by adding a docstring before the `@unit` call requires Unitful 1.10 or later. The `autodocs` argument also requires Unitful 1.10 or later.


Returns the [`Unitful.FreeUnits`](@ref) object to which `symb` is bound.

Usage example: `@unit mi "mi" Mile (201168//125)*m false`

This example will *not* generate `kmi` (kilomiles).
