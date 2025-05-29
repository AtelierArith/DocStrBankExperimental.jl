```
valueInUnitsOf(quantityArray::AbstractQuantityArray, simpleQuantity::SimpleQuantity)
```

Returns the numerical value of `quantityArray` expressed in units of `simpleQuantity`.

The result is equivalent to `valueOfDimensionless(quantityArray / simpleQuantity)`.

# Raises Exceptions

  * `Alicorn.Exceptions.DimensionMismatchError`: if the dimensions of `quantityArray` and `simpleQuantity` do not agree
