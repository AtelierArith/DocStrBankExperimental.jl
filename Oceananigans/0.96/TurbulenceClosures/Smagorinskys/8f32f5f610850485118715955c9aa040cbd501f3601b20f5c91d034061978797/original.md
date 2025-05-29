```
SmagorinskyLilly([time_discretization::TD = ExplicitTimeDiscretization(), FT=Float64;] C=0.16, Cb=1.0, Pr=1.0)
```

Return a `SmagorinskyLilly` type associated with the turbulence closure proposed by [Lilly62](@citet), [Smagorinsky1958](@citet), [Smagorinsky1963](@citet), and [Lilly66](@citet), which has an eddy viscosity of the form

```
νₑ = (Cˢ * Δᶠ)² * √(2Σ²) * √(1 - Cb * N² / Σ²)
```

and an eddy diffusivity of the form

```
κₑ = νₑ / Pr
```

where `Δᶠ` is the filter width, `Σ² = ΣᵢⱼΣᵢⱼ` is the double dot product of the strain tensor `Σᵢⱼ`, `Pr` is the turbulent Prandtl number, `N²` is the total buoyancy gradient, and `Cb` is a constant the multiplies the Richardson number modification to the eddy viscosity.

# Arguments

  * `time_discretization`: Either `ExplicitTimeDiscretization()` or `VerticallyImplicitTimeDiscretization()`,                        which integrates the terms involving only $z$-derivatives in the                        viscous and diffusive fluxes with an implicit time discretization.                        Default `ExplicitTimeDiscretization()`.
  * `FT`: Float type; default `Float64`.

# Keyword arguments

  * `Cˢ`: Smagorinsky coefficient. Default value is 0.16 as obtained by Lilly (1966).
  * `Cb`: Buoyancy term multipler based on Lilly (1962) (`Cb = 0` turns it off, `Cb ≠ 0` turns it on.       Typically, and according to the original work by Lilly (1962), `Cb = 1 / Pr`.)
  * `Pr`: Turbulent Prandtl numbers for each tracer. Either a constant applied to every       tracer, or a `NamedTuple` with fields for each tracer individually.

# References

Smagorinsky, J. "On the numerical integration of the primitive equations of motion for     baroclinic flow in a closed region." Monthly Weather Review (1958)

Lilly, D. K. "On the numerical simulation of buoyant convection." Tellus (1962)

Smagorinsky, J. "General circulation experiments with the primitive equations: I.     The basic experiment." Monthly Weather Review (1963)

Lilly, D. K. "The representation of small-scale turbulence in numerical simulation experiments."     NCAR Manuscript No. 281, 0, (1966)
