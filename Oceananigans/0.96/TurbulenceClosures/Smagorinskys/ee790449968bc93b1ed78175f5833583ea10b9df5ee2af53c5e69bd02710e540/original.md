```
Smagorinsky([time_discretization::TD = ExplicitTimeDiscretization(), FT=Float64;]
            coefficient = 0.16,
            Pr = 1.0)
```

Return a `Smagorinsky` type associated with the turbulence closure proposed by [Smagorinsky1958](@citet) and [Smagorinsky1963](@citet) which has an eddy viscosity of the form

```
νₑ = (Cˢ * Δᶠ)² * √(2Σ²)
```

and an eddy diffusivity of the form

```
κₑ = νₑ / Pr.
```

where `Δᶠ` is the filter width, `Σ² = ΣᵢⱼΣᵢⱼ` is the double dot product of the strain tensor `Σᵢⱼ`, `Pr` is the turbulent Prandtl number, `N²` is the total buoyancy gradient, and `Cb` is a constant the multiplies the Richardson number modification to the eddy viscosity.

`Cˢ` is the Smagorinsky coefficient and the default value is 0.16, according to the analysis by [Lilly66](@citet). For other options, see `LillyCoefficient` and `DynamicCoefficient`.
