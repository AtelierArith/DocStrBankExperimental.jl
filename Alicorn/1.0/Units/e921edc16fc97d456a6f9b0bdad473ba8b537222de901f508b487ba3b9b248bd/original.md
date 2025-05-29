```
Unit <: AbstractUnit
```

A composite unit formed by several [`UnitFactor`](@ref) objects.

# Fields

  * `unitFactors::Vector{UnitFactor}`: ordered list of [`UnitFactor`](@ref) objects that form the `Unit` through multiplication (concatenation).

# Constructors

```
Unit(unitFactors::Vector{UnitFactor})
Unit(abstractUnit::AbstractUnit)
Unit()
```

# Remarks

The constructor `Unit(abstractUnit::AbstractUnit)` is equivalent to [`convertToUnit(abstractUnit::AbstractUnit)`](@ref). The constructor `Unit()` returns the constant [`unitlessUnit`](@ref).

When a `Unit` is initialized, `UnitFactor` objects are added to the `unitFactors` field in order of appearance. `UnitFactor` objects with the same base (`UnitPrefix` and `BaseUnit`) are merged.

# Examples

1. The unit $\sqrt{\mathrm{Hz}}/\mathrm{nm}$ (square root of hertz per nanometer) can be constructed using the constructor method as follows:

    ```jldoctest
    julia> ucat = UnitCatalogue();

    julia> sqrtHz = UnitFactor(ucat.hertz, 1/2)
    UnitFactor Hz^5e-1

    julia> per_nm = UnitFactor(ucat.nano, ucat.meter, -1)
    UnitFactor nm^-1

    julia> sqrtHz_per_nm = Unit([sqrtHz, per_nm])
    Unit Hz^5e-1 nm^-1
    ```
2. Alternatively, $\sqrt{\mathrm{Hz}}/\mathrm{nm}$ can also be constructed arithmetically:

    ```jldoctest
    julia> ucat = UnitCatalogue();

    julia> sqrtHz_per_nm = sqrt(ucat.hertz) / ( ucat.nano * ucat.meter )
    Unit Hz^5e-1 nm^-1
    ```
