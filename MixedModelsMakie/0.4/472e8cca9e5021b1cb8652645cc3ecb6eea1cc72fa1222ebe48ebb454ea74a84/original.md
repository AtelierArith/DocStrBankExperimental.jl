```
caterpillar(m::MixedModel, gf::Symbol; kwargs...)
```

Returns a `Figure` of a "caterpillar plot" of the random-effects means and prediction intervals

A "caterpillar plot" is a horizontal error-bar plot of conditional means and standard deviations of the random effects.

`gf` specifies which grouping variable is displayed.

`kwargs...` are passed on to [`caterpillar!`](@ref).
