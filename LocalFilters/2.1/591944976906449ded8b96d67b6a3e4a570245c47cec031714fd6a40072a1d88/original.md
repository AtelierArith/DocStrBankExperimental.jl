```
kernel([Dims{N},] args...)
```

yields an `N`-dimensional abstract array built from `args...` and which can be used as a kernel in local filtering operations. The kernel is called a *neighborhood*, a *sliding window*, or a *structuring element* when its element are of type `Bool` and indicate whether a cell is to be considered. A *box* is a kernel whose elements are all `true`, it corresponds to an hyper-rectangular neighborhood whose sides are aligned with the Cartesian axes.

  * If `args...` is composed of `N` integers and/or ranges or if it is an `N`-tuple of integers and/or ranges, a *box* is returned whose axes are specified by `args...`. Each integer argument is converted in a centered unit range of this length (see [`LocalFilters.kernel_range`](@ref)).
  * If `Dims{N}` is provided and `args...` is a single integer or range, it is interpreted as being the same for all dimensions of an `N`-dimensional kernel. For example, `kernel(Dims{3},5)` yields a 3-dimensional *box* with index range `-2:2` in every dimension.
  * If `args...` is two Cartesian indices or a 2-tuple of Cartesian indices, say `start` and `stop`, a *box* is returned whose first and last indices are `start` and `stop`.
  * If `args...` is a Cartesian range, say `R::CartesianIndices{N}`, a *box* array is returned whose axes are given by `R`.
  * If `args...` is an abstract array of any other type than `CartesianIndices`, it is returned unchanged.

Optional leading argument `Dims{N}` can be specified to assert the number of dimensions of the result or to provide the number of dimensions when it cannot be inferred from the arguments. For example, when `args...` is a single integer length or range which should be interpreted as being the same for all dimensions.

See also [`LocalFilters.strel`](@ref), [`LocalFilters.ball`](@ref), [`LocalFilters.kernel_range`](@ref), and [`LocalFilters.reverse_kernel`](@ref).
