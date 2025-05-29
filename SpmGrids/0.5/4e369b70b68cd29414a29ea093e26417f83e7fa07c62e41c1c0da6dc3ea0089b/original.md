```
deconvolve_force!(grid::SpmGrid, response_channel::String,
    f₀::Float64=0., A::Float64=0., k::Float64=1800.;
    sweep_channel::String="", bwd::Bool=true)::Nothing
```

Applies the [Sadar Jarvis force deconvolution algorithm](https://aip.scitation.org/doi/10.1063/1.1667267) as implemented in the [SpmSpectroscopy](https://github.com/alexriss/SpmSpectroscopy.jl) package to each point in the `grid`. `response_channel` should refer to the "Frequency Shift" channel and `sweep_channel` (which defaults to the sweep signal of the grid) should be tip height "Z".

In addition, the along the experimental parameters `f₀` (resonance frequency), `A` (oscillation amplitude), and `k` (cantilever stiffness) can be specified. For `k` the default values is 1800 N/m, which is a typical value for [qPlus sensors](https://doi.org/10.1063/1.5052264). If the values for `f₀` and `A` are left at their default values of `0.`, the values will be extracted from the header data.

Adds the channels `"Force z"` and `"Potential"` to the SpmGrid `grid`. Additionally, the channels `"Force x"` and `"Force y"` will be calculated by differentiation of the  Potential in x and y direction, respectively. The x and y force components will not be calculated if the `sweep_channel` is not sorted.

If `bwd` is `true` (default), the plot will include data from backward sweep as well (if they exist).
