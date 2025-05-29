```
AnisotropicMinimumDissipation([time_discretization = ExplicitTimeDiscretization, FT = Float64;]
                              C = 1/3, Cν = nothing, Cκ = nothing, Cb = nothing)
```

Return parameters of type `FT` for the `AnisotropicMinimumDissipation` turbulence closure.

# Arguments

  * `time_discretization`: Either `ExplicitTimeDiscretization()` or `VerticallyImplicitTimeDiscretization()`,                        which integrates the terms involving only $z$-derivatives in the                        viscous and diffusive fluxes with an implicit time discretization.                        Default `ExplicitTimeDiscretization()`.
  * `FT`: Float type; default `Float64`.

# Keyword arguments

  * `C`: Poincaré constant for both eddy viscosity and eddy diffusivities. `C` is overridden      for eddy viscosity or eddy diffusivity if `Cν` or `Cκ` are set, respectively.
  * `Cν`: Poincaré constant for momentum eddy viscosity.
  * `Cκ`: Poincaré constant for tracer eddy diffusivities. If one number or function, the same       number or function is applied to all tracers. If a `NamedTuple`, it must possess       a field specifying the Poncaré constant for every tracer.
  * `Cb`: Buoyancy modification multiplier (`Cb = nothing` turns it off, `Cb = 1` was used by [Abkar16](@citet)).       *Note*: that we *do not* subtract the horizontally-average component before computing this       buoyancy modification term. This implementation differs from [Abkar16](@citet)'s proposal       and the impact of this approximation has not been tested or validated.

By default: `C = Cν = Cκ = 1/3`, and `Cb = nothing`, which turns off the buoyancy modification term. The default Poincaré constant is found by discretizing subgrid scale energy production, assuming a second-order advection scheme. [Verstappen14](@citet) show that the Poincaré constant should be 4 times larger than for straightforward (spectral) discretisation, resulting in `C = 1/3` in our formulation. They also empirically demonstrated that this coefficient produces the correct discrete production-dissipation balance. We further demonstrated this in https://github.com/CliMA/Oceananigans.jl/issues/4367.

`C`, `Cν` and `Cκ` may be numbers, or functions of `x, y, z`.

# Examples

```jldoctest
julia> using Oceananigans

julia> pretty_diffusive_closure = AnisotropicMinimumDissipation(C=1/2)
AnisotropicMinimumDissipation{ExplicitTimeDiscretization} turbulence closure with:
           Poincaré constant for momentum eddy viscosity Cν: 0.5
    Poincaré constant for tracer(s) eddy diffusivit(ies) Cκ: 0.5
                        Buoyancy modification multiplier Cb: nothing
```

```jldoctest
julia> using Oceananigans

julia> const Δz = 0.5; # grid resolution at surface

julia> surface_enhanced_tracer_C(x, y, z) = 1/12 * (1 + exp((z + Δz/2) / 8Δz));

julia> fancy_closure = AnisotropicMinimumDissipation(Cκ=surface_enhanced_tracer_C)
AnisotropicMinimumDissipation{ExplicitTimeDiscretization} turbulence closure with:
           Poincaré constant for momentum eddy viscosity Cν: 0.3333333333333333
    Poincaré constant for tracer(s) eddy diffusivit(ies) Cκ: surface_enhanced_tracer_C
                        Buoyancy modification multiplier Cb: nothing
```

```jldoctest
julia> using Oceananigans

julia> tracer_specific_closure = AnisotropicMinimumDissipation(Cκ=(c₁=1/12, c₂=1/6))
AnisotropicMinimumDissipation{ExplicitTimeDiscretization} turbulence closure with:
           Poincaré constant for momentum eddy viscosity Cν: 0.3333333333333333
    Poincaré constant for tracer(s) eddy diffusivit(ies) Cκ: (c₁ = 0.08333333333333333, c₂ = 0.16666666666666666)
                        Buoyancy modification multiplier Cb: nothing
```

# References

Verstappen, R., Rozema, W., and Bae, J. H. (2014), "Numerical scale separation in large-eddy     simulation", Center for Turbulence ResearchProceedings of the Summer Program 2014.

Vreugdenhil C., and Taylor J. (2018), "Large-eddy simulations of stratified plane Couette     flow using the anisotropic minimum-dissipation model", Physics of Fluids 30, 085104.

Verstappen, R. (2018), "How much eddy dissipation is needed to counterbalance the nonlinear     production of small, unresolved scales in a large-eddy simulation of turbulence?",     Computers & Fluids 176, pp. 276-284.
