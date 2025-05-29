```
arecompatible(x::OutputVar, y::OutputVar)
```

Return whether two `OutputVar` are defined on the same physical space

This is accomplished by comparing `dims` and `dim_attributes` (the latter because they might contain information about the units).

We assume that:

  * `dim2index` and `index2dim` where correctly created and they reflect `dims`
  * `data` is also consistent with `dims`,

We also *do not* check units for `data`.
