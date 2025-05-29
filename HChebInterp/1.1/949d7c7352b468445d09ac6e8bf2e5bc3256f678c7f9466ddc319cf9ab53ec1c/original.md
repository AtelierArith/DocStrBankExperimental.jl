```
hchebinterp(f, a, b, [criterion=SpectralError()]; order=defaultorder(criterion), atol=0, rtol=0, norm=norm, maxevals=typemax(Int), initdiv=1, reuse=true)
```

Return a piecewise polynomial interpolant of `f` on the interval $[a,b]$ of degree `order` that is pointwise accurate to the requested tolerances. Uses `criterion::AbstractAdaptCriterion` to estimate the interpolant error for h-adaptation. By default, the `order` for `SpectralError()` is 15 and for `HAdaptError()` is 4.

!!! note "HChebInterp 1.1"
    The `reuse` keyword requires at least HChebInterp v1.1.


The keyword `reuse` specifies that the algorithm will reuse function evaluations on the interpolation grid whenever possible. For expensive functions and interpolation problems on the order of seconds, the benefit will be noticeable, i.e. roughly a 12% saving in function evaluations for the default solver. Since looking up the interpolation points is not necessarily fast, `reuse=false` can be set to turn off this optimization.
