```
UnitFactor <: AbstractUnit
```

A composite unit formed by a named unit of type [`BaseUnit`](@ref), a prefix of type [`UnitPrefix`](@ref) modifying it, and an exponent indicating to which power the pair is raised.

# Fields

  * `unitPrefix::UnitPrefix`
  * `baseUnit::BaseUnit`
  * `exponent::Real`

# Constructors

```
UnitFactor(unitPrefix::UnitPrefix, baseUnit::BaseUnit, exponent::Real)
UnitFactor(baseUnit::BaseUnit, exponent::Real)
UnitFactor(unitPrefix::UnitPrefix, baseUnit::BaseUnit)
UnitFactor(baseUnit::BaseUnit)
UnitFactor()
```

If any of the three fields are omitted from the constructor call, that field is initialized using the corresponding default value:

  * `unitPrefix = unitPrefix=Alicorn.emptyUnitPrefix`
  * `baseUnit = Alicorn.unitlessBaseUnit`
  * `exponent = 1`

# Raises Exceptions

  * `Core.DomainError`: if attempting to initialize the `exponent` field with an infinite number

# Remarks

The constructor converts the exponent to `Int` if possible. If `baseUnit=Alicorn.unitlessBaseUnit`, the prefix is always set to `unitPrefix=Alicorn.emptyUnitPrefix` and the exponent to `exponent=1`.

# Examples

1. The unit $\mathrm{km}^2$ (square kilometer) can be represented by a `UnitFactor` that can be constructed using the type constructor method as follows:

    ```jldoctest
    julia> ucat = UnitCatalogue();

    julia> UnitFactor(ucat.kilo, ucat.meter, 2)
    UnitFactor km^2
    ```
2. Alternatively, $\mathrm{km}^2$ can be constructed arithmetically:

    ```jldoctest
    julia> ucat = UnitCatalogue();

    julia> (ucat.kilo * ucat.meter)^2
    UnitFactor km^2
    ```
