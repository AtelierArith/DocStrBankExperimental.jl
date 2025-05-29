```
DGMulti(approximation_type::AbstractDerivativeOperator;
        element_type::AbstractElemShape,
        surface_flux=flux_central,
        surface_integral=SurfaceIntegralWeakForm(surface_flux),
        volume_integral=VolumeIntegralWeakForm(),
        kwargs...)
```

Create a summation by parts (SBP) discretization on the given `element_type` using a tensor product structure based on the 1D SBP derivative operator passed as `approximation_type`.

For more info, see the documentations of [StartUpDG.jl](https://jlchan.github.io/StartUpDG.jl/dev/) and [SummationByPartsOperators.jl](https://ranocha.de/SummationByPartsOperators.jl/stable/).
