```
valueOfDimensionless(quantity::AbstractQuantity)
```

Strips the unit from a dimensionless quantity and returns its bare value.

# Raises Exceptions

  * `Alicorn.Exceptions.DimensionMismatchError`: if `quantity` is not dimensionless
