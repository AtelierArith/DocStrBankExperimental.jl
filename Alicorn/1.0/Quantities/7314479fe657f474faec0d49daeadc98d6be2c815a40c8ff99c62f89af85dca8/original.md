```
InternalUnits
```

A set of seven `SimpleQuantity` objects which represent a choice of units with respect to which the seven basic physical dimensions of the SI system are measured.

# Fields

  * `mass::SimpleQuantity`: unit of mass
  * `length::SimpleQuantity`: unit of length
  * `time::SimpleQuantity`: unit of time
  * `current::SimpleQuantity`: unit of current
  * `temperature::SimpleQuantity`: unit of temperature
  * `amount::SimpleQuantity`: unit of amount
  * `luminousIntensity::SimpleQuantity`: unit of luminousIntensity

# Constructors

```
InternalUnits(::SimpleQuantity, ::SimpleQuantity, ::SimpleQuantity, ::SimpleQuantity, ::SimpleQuantity, ::SimpleQuantity, ::SimpleQuantity)
InternalUnits(; mass = 1*kilogram, length = 1*meter, time = 1*second, current = 1*ampere,temperature = 1*kelvin, amount = 1*mol, luminousIntensity = 1*candela)

# Raises Exceptions
- `Core.DomainError`: if attempting to initialize any field with a quantity
of a value that is zero, infinite, or not real
- `Exceptions.DimensionMismatchError`: if attempting to initialize any field
with a quantity whose dimension does not match the physical dimension the field
represents

# Examples
The following `InternalUnits` measure lengths in units of ``3 cm`` and uses
the basic SI units for all other dimensions:
```

jldoctest julia> ucat = UnitCatalogue(); cm = ucat.centi * ucat.meter ;

julia> InternalUnits(length = 3cm) InternalUnits  mass unit:               1 kg  length unit:             3 cm  time unit:               1 s  current unit:            1 A  temperature unit:        1 K  amount unit:             1 mol  luminous intensity unit: 1 cd ```
