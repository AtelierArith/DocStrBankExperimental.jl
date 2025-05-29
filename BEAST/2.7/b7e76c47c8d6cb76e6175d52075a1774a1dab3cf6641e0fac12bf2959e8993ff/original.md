```
scalartype(x)
```

The scalar field over which the values of a global or local basis function, or an operator are defined. This should always be a scalar type, even if the basis or operator takes on values in a vector or tensor space. This data type is used to determine the `eltype` of assembled discrete operators.
