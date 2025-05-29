```
inUnitsOf(qArray::AbstractQuantityArray, unit::AbstractUnit)::SimpleQuantityArray
```

Express `qArray` as an object of type `SimpleQuantityArray` in terms of the unit specified by `unit`.

# Raises Exceptions

  * `Alicorn.Exceptions.DimensionMismatchError`: if the dimensions of `qArray` and `unit` do not agree
