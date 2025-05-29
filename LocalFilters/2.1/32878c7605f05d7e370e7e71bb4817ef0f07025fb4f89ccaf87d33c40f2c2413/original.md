```
erode(A, B=3; order=FORWARD_FILTER, slow=false) -> Amin
```

yields the erosion of `A` by the structuring element defined by `B`. The returned result, `Amin`, is similar to `A` (same size and type) and its values are the local minima of `A` in the neighborhood defined by `B`.

Keyword `order` specifies the filter direction, `FORWARD_FILTER` by default.

If `B` is not an `N`-dimensional array, [`kernel(Dims{N},B)`](@ref) is called to build a kernel with `N = ndims(A)` the number of dimensions of `A`.

If the structuring element `B` is equivalent to a simple hyper-rectangular sliding window (which is the case by default) and unless keyword `slow` is true, the much faster van Herk-Gil-Werman algorithm is used.

An erosion is one of the most basic operations of mathematical morphology. See [`erode!`](@ref) for an in-place version of the method, [`dilate`](@ref) for retrieving the local maxima, and [`localextrema`](@ref) for performing an erosion and a dilation in a single pass.
