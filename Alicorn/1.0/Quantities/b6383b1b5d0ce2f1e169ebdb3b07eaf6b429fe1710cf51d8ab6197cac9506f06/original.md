```
valueOfDimensionless(qArray::AbstractQuantityArray)
```

Strips the unit from a dimensionless quantity array and returns its bare value.

# Raises Exceptions

  * `Alicorn.Exceptions.DimensionMismatchError`: if `qArray` is not dimensionless
