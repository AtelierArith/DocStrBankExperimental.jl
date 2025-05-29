```
rectangular_window_weight(xs::AbstractArray, xlims::AbstractVector,
                          ylims::AbstractVector, α::Number)
```

A simple boundary weighting function for `kernel_eigs` and `kernel_bvp`. Returns a weight that is approximately 1 outside of `xlims` × `ylims` and 0 inside via the a function of logistic functions.

Arguments:

  * `xs`: A `d` × `N` array of points, where `d` is the size of the phase space and `N` is the number of points.
  * `xlims` and `ylims`: 2-vectors giving the rectangle where the weight is approximately 0
  * `α`: The length scale of the logistic functions (typically small relative to the size of the domain)

Output:

  * `w`: A `N`-vector with the window weights
