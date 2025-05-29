```
valueInUnitsOf(quantity::AbstractQuantity, simpleQuantity::SimpleQuantity)
```

Returns the numerical value of `quantity` expressed in units of `simpleQuantity`.

The result is equivalent to `valueOfDimensionless(quantity / simpleQuantity)`.

# Raises Exceptions

  * `Alicorn.Exceptions.DimensionMismatchError`: if the dimensions of `quantity` and `simpleQuantity` do not agree
