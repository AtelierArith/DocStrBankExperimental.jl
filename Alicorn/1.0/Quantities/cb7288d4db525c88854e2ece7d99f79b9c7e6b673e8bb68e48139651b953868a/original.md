```
SimpleQuantityArray(quantityArray::AbstractQuantityArray)
```

Construct a `SimpleQuantityArray` from a physical quantity of any implementation of `AbstractQuantityArray`.

If `quantityArray` is of type `SimpleQuantityArray`, it is returned unchanged. If `quantityArray` is of type `QuantityArray`, it is expressed in terms of the SI units specified by `quantityArray.InternalUnits`.
