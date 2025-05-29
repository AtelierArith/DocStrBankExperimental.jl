```
Quantity(::AbstractQuantity, ::InternalUnits)
Quantity(::AbstractQuantity)
```

Construct a `Quantity` from a physical quantity of any implementation of `AbstractQuantity`.

If no `InternalUnits` are specified, they are constructed using basic SI units.
