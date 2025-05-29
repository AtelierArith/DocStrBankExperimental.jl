```
ConvectiveAdjustmentVerticalDiffusivity([time_discretization = VerticallyImplicitTimeDiscretization(), FT=Float64;]
                                        convective_κz = 0,
                                        convective_νz = 0,
                                        background_κz = 0,
                                        background_νz = 0)
```

Return a convective adjustment vertical diffusivity closure that applies different values of diffusivity and/or viscosity depending whether the region is statically stable (positive or zero buoyancy gradient) or statically unstable (negative buoyancy gradient).

# Arguments

  * `time_discretization`: Either `ExplicitTimeDiscretization()` or `VerticallyImplicitTimeDiscretization()`;                        default `VerticallyImplicitTimeDiscretization()`.
  * `FT`: Float type; default `Float64`.

# Keyword arguments

  * `convective_κz`: Vertical tracer diffusivity in regions with negative (unstable) buoyancy gradients. Either                  a single number, function, array, field, or tuple of diffusivities for each tracer.
  * `background_κz`: Vertical tracer diffusivity in regions with zero or positive (stable) buoyancy gradients.
  * `convective_νz`: Vertical viscosity in regions with negative (unstable) buoyancy gradients. Either                 a number, function, array, or field.
  * `background_κz`: Vertical viscosity in regions with zero or positive (stable) buoyancy gradients.

# Example

```jldoctest
julia> using Oceananigans

julia> cavd = ConvectiveAdjustmentVerticalDiffusivity(convective_κz = 1)
ConvectiveAdjustmentVerticalDiffusivity{VerticallyImplicitTimeDiscretization}(background_κz=0.0 convective_κz=1 background_νz=0.0 convective_νz=0.0)
```
