```
unwrap(m; kwargs...)
```

Assumes `m` to be a sequence of values that has been wrapped to be inside the given `range` (centered around zero), and undoes the wrapping by identifying discontinuities. If a single dimension is passed to `dims`, then `m` is assumed to have wrapping discontinuities only along that dimension. If a range of dimensions, as in `1:ndims(m)`, is passed to `dims`, then `m` is assumed to have wrapping discontinuities across all `ndims(m)` dimensions.

A common usage for unwrapping across a singleton dimension is for a phase measurement over time, such as when comparing successive frames of a short-time-fourier-transform, as each frame is wrapped to stay within (-pi, pi].

A common usage for unwrapping across multiple dimensions is for a phase measurement of a scene, such as when retrieving the phase information of of an image, as each pixel is wrapped to stay within (-pi, pi].

# Arguments

  * `m::AbstractArray{T, N}`: Array to unwrap.
  * `dims=nothing`: Dimensions along which to unwrap. If `dims` is an integer, then   `unwrap` is called on that dimension. If `dims=1:ndims(m)`, then `m` is unwrapped   across all dimensions.
  * `range=2pi`: Range of wrapped array.
  * `circular_dims=(false, ...)`:  When an element of this tuple is `true`, the   unwrapping process will consider the edges along the corresponding axis   of the array to be connected.
  * `rng=GLOBAL_RNG`: Unwrapping of arrays with dimension > 1 uses a random   initialization. A user can pass their own RNG through this argument.
