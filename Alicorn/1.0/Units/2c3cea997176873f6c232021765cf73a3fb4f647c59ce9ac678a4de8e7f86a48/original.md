```
UnitCatalogue
```

Collection of [`UnitFactorElement`](@ref) objects. These include unit prefixes of type [`UnitPrefix`](@ref) and named units of type [`BaseUnit`](@ref).

A single `UnitCatalogue` object serves as a consistent library of unit elements. Users can construct composite units based on the prefix and unit definitions stored in the unit catalogue. In most use cases, it is sufficient to initialize a single unit catalogue using `UnitCatalogue()`. The returned catalogue contains the unit prefixes and named units accepted for use with the International System of Units.

Unit prefixes and base units stored in a unit catalogue can be accessed using dot notation through [`Base.getproperty`](@ref) using their `name` field. In consequence, the names of elements stored in the unit catalogue have to be unique.

# Fields

The fields of `UnitCatalogue` are not considered part of the public interface and cannot be accessed using the dot notation. The stored [`UnitFactorElement`](@ref) objects can be accessed through the following methods:

  * [`Base.getproperty(unitCatalogue::UnitCatalogue, symbol::Symbol)`](@ref)
  * [`listUnitPrefixes(unitCatalogue::UnitCatalogue)`](@ref)
  * [`listBaseUnits(unitCatalogue::UnitCatalogue)`](@ref)
  * [`listUnitPrefixNames(unitCatalogue::UnitCatalogue)`](@ref)
  * [`listBaseUnitNames(unitCatalogue::UnitCatalogue)`](@ref)
  * [`providesUnitPrefix(unitCatalogue::UnitCatalogue, symbol::String)`](@ref)
  * [`providesBaseUnit(unitCatalogue::UnitCatalogue, symbol::String)`](@ref)
  * [`add!(unitCatalogue::UnitCatalogue, unitPrefix::UnitPrefix)`](@ref)
  * [`add!(unitCatalogue::UnitCatalogue, baseUnit::BaseUnit)`](@ref)
  * [`remove!(unitCatalogue::UnitCatalogue, elementName::String)`](@ref)

# Constructors

```
UnitCatalogue(unitPrefixes::Vector{UnitPrefix}, baseUnits::Vector{BaseUnit})
UnitCatalogue(unitPrefixes::Vector, baseUnits::Vector)
UnitCatalogue()
```

# Raises exceptions

  * `Alicorn.Exceptions.DuplicationError`: if attempting to add [`UnitFactorElement`](@ref) objects with identical `name` fields to the `UnitCatalogue`

# Remarks

If vectors of types other than [`UnitPrefix`](@ref) and [`BaseUnit`](@ref) are provided, the constructor attempts to convert them to those types.

If the constructor is invoked without arguments, the default set of unit prefix and base unit definitions is added to the `UnitCatalogue`.

# Examples

1. Initialize a default unit catalogue (containing the standard unit prefixes and named units accepted for use with the International System of Units) and use it to define the unit $\mathrm{nm}$ (nanometer):

    ```jldoctest
    julia> ucat = UnitCatalogue()
    UnitCatalogue providing
     21 unit prefixes
     43 base units

    julia> nm = ucat.nano * ucat.meter
    UnitFactor nm
    ```
2. Initialize an empty unit catalogue (to be filled with custom prefix and unit definitions) and add new prefix with name `nano`:

    ```jldoctest
    julia> ucat = UnitCatalogue([], [])
    UnitCatalogue providing
     0 unit prefixes
     0 base units

    julia> nano = UnitPrefix(name="nano", symbol="n", value=1e-9)
    UnitPrefix nano (n) of value 1e-9

    julia> add!(ucat, nano)
    UnitCatalogue providing
     1 unit prefixes
     0 base units

    julia> ucat.nano
    UnitPrefix nano (n) of value 1e-9
    ```
