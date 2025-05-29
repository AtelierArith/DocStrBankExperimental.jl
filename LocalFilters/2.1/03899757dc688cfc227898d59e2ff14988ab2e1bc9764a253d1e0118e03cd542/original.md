```
dilate(A, B=3; order=FORWARD_FILTER, slow=false) -> Amax
```

yields the dilation of `A` by the structuring element defined by `B`. The returned result, `Amax`, is similar to `A` (same size and type) and its values are the local maxima of `A` in the neighborhood defined by `B`.

Keyword `order` specifies the filter direction, `FORWARD_FILTER` by default.

If `B` is not an `N`-dimensional array, [`kernel(Dims{N},B)`](@ref) is called to build a kernel with `N = ndims(A)` the number of dimensions of `A`.

If the structuring element `B` is equivalent to a simple hyper-rectangular sliding window (which is the case by default) and unless keyword `slow` is true, the much faster van Herk-Gil-Werman algorithm is used.

A dilation is one of the most basic operations of mathematical morphology. See [`dilate!`](@ref) for an in-place version of the method, [`erode`](@ref) for retrieving the local minima, and [`localextrema`](@ref) for performing an erosion and a dilation in a single pass.
