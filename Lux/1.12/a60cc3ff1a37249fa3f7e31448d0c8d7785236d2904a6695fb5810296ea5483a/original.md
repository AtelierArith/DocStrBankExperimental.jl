```
SelectDim(dim, i)
```

Return a view of all the data of the input `x` where the index for dimension `dim` equals `i`. Equivalent to `view(x,:,:,...,i,:,:,...)` where `i` is in position `d`.

## Arguments

  * `dim`: Dimension for indexing
  * `i`: Index for dimension `dim`

## Inputs

  * `x`: AbstractArray that can be indexed with `view(x,:,:,...,i,:,:,...)`

## Returns

  * `view(x,:,:,...,i,:,:,...)` where `i` is in position `d`
  * Empty `NamedTuple()`
