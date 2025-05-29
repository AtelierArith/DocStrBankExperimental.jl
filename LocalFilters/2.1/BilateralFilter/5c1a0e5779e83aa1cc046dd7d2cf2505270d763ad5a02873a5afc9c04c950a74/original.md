```
bilateralfilter([T = float(eltype(A)),] A, F, G...=3; order = FORWARD_FILTER)
```

yields the result of applying the bilateral filter on array `A`.

Argument `F` specifies how to smooth the differences in values. It can be:

  * a function, say `f`, which is called as `f(A[i],A[j])` to yield a nonnegative weight for `i` the central index and `j` the index in a nearby position;
  * a positive real, say `σ`, which is assumed to be the standard deviation of a Gaussian.

Arguments `G, ...` specify the settings of the distance filter for smoothing differences in coordinates. There are several possibilities:

  * `G... = wgt` an array of nonnegative weights or of Booleans. The axes of `wgt` must have offsets so that the zero index is part of the indices of `wgt`.
  * `G... = f, w` with `f` a function and `w` any kind of argument that can be used to build a window `win` specifying the extension of the neighborhood. The value of the distance filter will be `max(f(i),0)` for all Cartesian index `i` of `win` such that `win[i]` is true. See [`kernel`](@ref) for the different ways to specify a window.
  * `G... = σ` or , `G... = σ, w` with `σ` a positive real assumed to be the standard deviation of a Gaussian function and `w` any kind of argument that can be used to build a window `win` specifying the extension of the neighborhood. If `w` is not specified, a default window of size `±3σ` is assumed.

Optional argument `T` is to specify the element type of the result. This is needed if the default is unsuitable.

See [`bilateralfilter!`](@ref) for an in-place version of this function and see [Wikipedia](https://en.wikipedia.org/wiki/Bilateral_filter) for a description of the bilateral filter.
