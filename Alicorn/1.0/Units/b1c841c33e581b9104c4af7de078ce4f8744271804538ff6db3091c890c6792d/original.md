```
UnitPrefix  <: AbstractUnitElement
```

Metric prefix that can precede a base unit. The prefix indicates that the unit is scaled by a corresponding factor.

# Fields

  * `name::String`: long form name of the prefix
  * `symbol::String`: short symbol used to denote the prefix in a composite unit
  * `value`: numerical value of the prefix

# Constructor

```
UnitPrefix(;name::String, symbol::String, value::Real)
```

The string `name` needs to be valid as an identifier. The number `value` needs to be finite.

# Raises Exceptions

  * `Core.ArgumentError`: if attempting to initialize the `name` field with a string that is not valid as an identifier
  * `Core.DomainError`: if attempting to initialize the `value` field with an infinite number

# Examples

The prefix "milli" for the International System of Units is by default defined in Alicorn as

```jldoctest
julia> UnitPrefix(name="milli", symbol="m", value=1e-3)
UnitPrefix milli (m) of value 1e-3
```
