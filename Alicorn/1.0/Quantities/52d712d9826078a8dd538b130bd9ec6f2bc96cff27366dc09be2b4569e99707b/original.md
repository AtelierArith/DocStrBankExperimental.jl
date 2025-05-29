```
inInternalUnitsOf(qArray::QuantityArray{T}, targetIntU::InternalUnits) where T
```

Returns a new `QuantityArray` corresponding to `qArray`, but stored using `targetIntU` as new internal units.

The value type `S` of the returned quantity array is identical to `T`, if possible.
