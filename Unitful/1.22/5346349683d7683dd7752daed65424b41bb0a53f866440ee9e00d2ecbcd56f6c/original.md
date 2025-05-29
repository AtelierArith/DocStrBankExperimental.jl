```
@dimension(symb, abbr, name, autodocs=false)
```

Creates new dimensions. `name` will be used like an identifier in the type parameter for a [`Unitful.Dimension`](@ref) object. `symb` will be a symbol defined in the namespace from which this macro is called that is bound to a [`Unitful.Dimensions`](@ref) object. For most intents and purposes it is this object that the user would manipulate in doing dimensional analysis. The symbol is not exported.

This macro extends [`Unitful.abbr`](@ref) to display the new dimension in an abbreviated format using the string `abbr`.

Type aliases are created that allow the user to dispatch on [`Unitful.Quantity`](@ref), [`Unitful.Level`](@ref) and [`Unitful.Units`](@ref) objects of the newly defined dimension. The type alias for quantities or levels is simply given by `name`, and the type alias for units is given by `name*"Units"`, e.g. `LengthUnits`. Note that there is also `LengthFreeUnits`, for example, which is an alias for dispatching on `FreeUnits` with length dimensions. The aliases are not exported. If `autodocs == true`, docstrings will be automatically generated for these aliases.

!!! compat "Unitful 1.10"
    Documenting the resulting dimension symbol by adding a docstring before the `@dimension` call requires Unitful 1.10 or later. The `autodocs` argument also requires Unitful 1.10 or later.


Finally, if you define new dimensions with [`@dimension`](@ref) you will need to specify a preferred unit for that dimension with [`Unitful.preferunits`](@ref), otherwise promotion will not work with that dimension. This is done automatically in the [`@refunit`](@ref) macro.

Returns the `Dimensions` object to which `symb` is bound.

Usage example from `src/pkgdefaults.jl`: `@dimension 𝐋 "𝐋" Length`
