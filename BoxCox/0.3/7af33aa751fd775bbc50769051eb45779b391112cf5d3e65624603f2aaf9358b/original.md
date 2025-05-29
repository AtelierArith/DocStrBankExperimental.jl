```
boxcoxplot(bc::PowerTransformation; kwargs...)
boxcoxplot!(axis::Axis, bc::PowerTransformation;
            λ=nothing, n_steps=21, xlabel="λ", ylabel="log likelihood",
            conf_level=nothing, attributes...)
```

Create a diagnostic plot for the Box-Cox transformation.

The mutating method for `Axis` returns the (modified) original `Axis`. The non-mutating method returns a `Figure`.

If λ is `nothing`, the range of possible values for the λ parameter is automatically determined, with a total of `n_steps`. If `λ` is a vector of numbers, then the λ parameter is evaluated at each element of that vector.

If `conf_level` is `nothing`, then no confidence interval is displayed.

`attributes` are forwarded to `scatterlines!`.

!!! note
    A meaningful plot is only possible when `bc` has not been `empty!`'ed.


!!! note
    The plotting functionality interface is defined as a package extension and only loaded when Makie is available. You must load an appropriate Makie backend (e.g., CairoMakie or GLMakie) to actually render a plot.

