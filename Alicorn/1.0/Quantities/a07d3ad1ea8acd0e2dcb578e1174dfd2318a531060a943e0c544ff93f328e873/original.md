```
valueInUnitsOf(qArray::AbstractQuantityArray, unit::AbstractUnit)
```

Returns the numerical value of `qArray` expressed in units of `unit`.

# Raises Exceptions

  * `Alicorn.Exceptions.DimensionMismatchError`: if the dimensions of `quantity` and `unit` do not agree
