```
QuantityArray(::AbstractQuantityArray, ::InternalUnits)
QuantityArray(::AbstractQuantityArray)
```

Construct a `QuantityArray` from a physical quantity of any implementation of `AbstractQuantityArray`.

If no `InternalUnits` are specified, they are inferred from the `AbstractQuantityArray` if possible. Else, basic SI units are used.
