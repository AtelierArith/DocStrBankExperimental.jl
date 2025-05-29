```
profile(m::Minuit, var; size=100, bound=2, grid=nothing, subtract_min=false)
```

Calculate 1D cost function profile over a range.

A 1D scan of the cost function around the minimum, useful to inspect the minimum. For a fit with several free parameters this is not the same as the Minos profile computed by `mncontour`.

## Arguments

  * `m::Minuit` : The Minuit object to minimize.
  * `var` : The parameter to scan over (name or index).
  * `size=100` : Number of scanning points. Ignored if `grid` is set.
  * `bound=2` : Number of `sigma`s to scan symmetrically around the minimum. Ignored if `grid` is set.
  * `grid::AbstractVector` : Grid points to scan over. If `grid` is set, `size` and `bound` are ignored.
  * `subtract_min::Bool=false` : Subtract minimum from return values.

## Returns

  * Tuple(`x`, `y`) : Tuple of 1D arrays with the parameter values and the function values.
