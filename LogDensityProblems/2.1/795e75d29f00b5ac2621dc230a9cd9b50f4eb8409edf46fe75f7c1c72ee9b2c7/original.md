```
logdensity(ℓ, x)
```

Evaluate the log density `ℓ` at `x`, which has length compatible with its [`dimension`](@ref).

Return a real number, which may or may not be finite (can also be `NaN`). Non-finite values other than `-Inf` are invalid but do not error, caller should deal with these appropriately.

# Note about constants

Log densities can be shifted by *the same constant*, as long as it is consistent between calls. For example,

```julia
logdensity(::StandardMultivariateNormal) = -0.5 * sum(abs2, x)
```

is a valid implementation for some callable `StandardMultivariateNormal` that would implement the standard multivariate normal distribution (dimension $k$) with pdf

$$
(2\pi)^{-k/2} e^{-x'x/2}
$$
