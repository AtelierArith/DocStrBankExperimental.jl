```
DimArray(f::Function, dim::Dimension; [name])
```

Apply function `f` across the values of the dimension `dim` (using `broadcast`), and return the result as a dimensional array with the given dimension. Optionally provide a name for the result.
