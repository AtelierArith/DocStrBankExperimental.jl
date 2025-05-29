```
SimpleQuantity{T<:Number} <: AbstractQuantity{T}
```

A physical quantity consisting of a scalar value and a physical unit.

# Fields

  * `value::T`: value of the quantity
  * `unit::Unit`: unit of the quantity

# Constructors

```
SimpleQuantity(::Number, ::AbstractUnit)
SimpleQuantity(::Number)
SimpleQuantity(::AbstractUnit)
```

If no unit is passed to the constructor, `unitlessUnit` is used by default. If no value is passed to the constructor, the value is set to 1 by default.

If called with a `Quantity` as argument, the `Quantity` is expressed in terms of the units used to store its value internally, see [`InternalUnits`](@ref).

```
SimpleQuantity(::Quantity)
```

If the type `T` is specified explicitly, Alicorn attempts to convert the `value` accordingly:

```
SimpleQuantity{T}(::Number, ::AbstractUnit) where {T<:Number}
SimpleQuantity{T}(::Number) where {T<:Number}
SimpleQuantity{T}(::AbstractUnit) where {T<:Number}
```

# Examples

1. The quantity $7\,\mathrm{nm}$ (seven nanometers) can be constructed using the constructor method as follows:

    ```jldoctest
    julia> ucat = UnitCatalogue() ;

    julia> nanometer = ucat.nano * ucat.meter
    UnitFactor nm

    julia> quantity = SimpleQuantity(7, nanometer)
    7 nm
    ```
2. Alternatively, $7\,\mathrm{nm}$ can be constructed arithmetically:

    ```jldoctest
    julia> ucat = UnitCatalogue() ;

    julia> nm = ucat.nano * ucat.meter
    UnitFactor nm

    julia> quantity = 7nm
    7 nm
    ```
