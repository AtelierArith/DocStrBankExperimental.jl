```
ScalarQuantity{T}
```

Type union representing a scalar (number) of type `T`, with or without a unit.

Alias for `Union{T, AbstractQuantity{T}} where T<:Number`.
