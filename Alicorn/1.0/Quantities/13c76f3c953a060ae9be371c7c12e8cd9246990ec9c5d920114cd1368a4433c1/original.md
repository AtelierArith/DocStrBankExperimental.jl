```
inInternalUnitsOf(quantity::Quantity{T}, targetIntU::InternalUnits) where T
```

Returns a new `Quantity{S}` corresponding to `quantity`, but stored using `targetIntU` as new internal units.

The value type `S` of the returned quantity is identical to `T`, if possible.
