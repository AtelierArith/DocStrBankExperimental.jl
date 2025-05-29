```
qqplot(x, y; kwargs...)
```

Draw a Q-Q plot, comparing quantiles of two distributions. `y` must be a list of samples, i.e., `AbstractVector{<:Real}`, whereas `x` can be

  * a list of samples,
  * an abstract distribution, e.g. `Normal(0, 1)`,
  * a distribution type, e.g. `Normal`.

In the last case, the distribution type is fitted to the data `y`.

The attribute `qqline` (defaults to `:none`) determines how to compute a fit line for the Q-Q plot. Possible values are the following.

  * `:identity` draws the identity line.
  * `:fit` computes a least squares line fit of the quantile pairs.
  * `:fitrobust` computes the line that passes through the first and third quartiles of the distributions.
  * `:none` omits drawing the line.

Broadly speaking, `qqline = :identity` is useful to see if `x` and `y` follow the same distribution, whereas `qqline = :fit` and `qqline = :fitrobust` are useful to see if the distribution of `y` can be obtained from the distribution of `x` via an affine transformation.

Graphical attributes are

  * `color` to control color of both line and markers (if `markercolor` is not specified)
  * `linestyle`
  * `linewidth`
  * `markercolor`
  * `strokecolor`
  * `strokewidth`
  * `marker`
  * `markersize`
