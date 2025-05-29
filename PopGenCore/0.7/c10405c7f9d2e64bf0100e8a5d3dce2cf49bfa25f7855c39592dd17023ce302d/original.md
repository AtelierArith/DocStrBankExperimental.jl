```
GenoArray::DataType
```

An alias for an `AbstractVector` of elements `Missing` and `Genotype`, which itself is of type `NTuple{N, <:Integer} where N`. The definition as an `AbstractVector` adds flexibility for `SubArray` cases.
