```
qqplot(x::AbstractVector{AbstractFloat}, y::AbstractVector{AbstractFloat}; kwargs...)
```

The qqplot function compares the quantiles of two distributions.

  * `qqline`: determines how to compute a fit line for the Q-Q plot. The options are

      * `identity`: draw the line y = x (the deafult).
      * `fit`: draw a least squares line fit of the quantile pairs.
      * `fitrobust` or `quantile`: draw the line that passes through the first and third quartiles of the distributions.
      * `none`: do not draw any line.

    Broadly speaking, `qqline=:identity` is useful to see if x and y follow the same distribution, whereas `qqline=:fit` and `qqline=:fitrobust` are useful to see if the distribution of y can be obtained from the distribution of x via an affine transformation.
  * For fine setting of the line and scatter points use the same options as in the `plot` module.

Examples:

```
qqplot(randn(100), randn(100), show=true)

qqplot(randn(100), show=true)
```
