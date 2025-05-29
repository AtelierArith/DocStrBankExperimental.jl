```
inUnitsOf(quantity::AbstractQuantity, unit::AbstractUnit)::SimpleQuantity
```

Express `quantity` as an object of type `SimpleQuantity` in terms of the unit specified by `unit`.

# Raises Exceptions

  * `Alicorn.Exceptions.DimensionMismatchError`: if the dimensions of `quantity` and `unit` do not agree
