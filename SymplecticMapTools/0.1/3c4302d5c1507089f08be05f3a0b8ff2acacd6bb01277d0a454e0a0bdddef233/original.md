```
window_weight(xs::AbstractArray, lims::AbstractVector, α::Number;
                   ind::Integer=2)
```

A simple boundary weighting function for `kernel_eigs` and `kernel_bvp`. Returns a weight that is approximately 1 outside of `lims` and 0 inside via the sum of two logistic functions.

Arguments:

  * `xs`: A `d` × `N` array of points, where `d` is the size of the phase space and `N` is the number of points.
  * `lims`: A 2-vector giving the interval where the weight is approximately 0
  * `α`: The length scale of the logistic functions (typically small relative to the size of the domain)
  * `ind=2`: The index over which the window is applied. Defaults to `2` for maps on T×R (such as the standard map)

Output:

  * `w`: A `N`-vector with the window weights
