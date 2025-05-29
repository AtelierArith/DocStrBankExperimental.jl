```
EasyRanges.normalize(x)
```

yields an object which represents the same (Cartesian) index or set of indices as `x` but in one of the following forms:

  * an integer `i::Int` if `x` is equivalent to a single linear index;
  * a range of integers `r::AbstractRange{Int}` if `x` is equivalent to a range of linear indices;
  * a multi-dimensional Cartesian index `I::CartesianIndex{N}` if `x` is equivalent to a single `N`-dimensional Cartesian index;
  * a multi-dimensional Cartesian range `R::CartesianIndices{N}` if `x` is equivalent to a rectangular region of `N`-dimensional Cartesian indices.

This method may be extended by foreign packages to let `EasyRanges` known how to deal with other types of indices or of set of indices provided they are equivalent to one of the above canonical forms.
