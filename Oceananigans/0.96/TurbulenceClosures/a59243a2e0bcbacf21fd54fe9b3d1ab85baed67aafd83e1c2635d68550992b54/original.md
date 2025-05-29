```
ScalarDiffusivity(time_discretization = ExplicitTimeDiscretization(),
                  formulation = ThreeDimensionalFormulation(), FT = Float64;
                  ν = 0,
                  κ = 0,
                  discrete_form = false,
                  loc = (nothing, nothing, nothing),
                  parameters = nothing)
```

Return `ScalarDiffusivity` turbulence closure with viscosity `ν` and tracer diffusivities `κ` for each tracer field in `tracers`. If a single `κ` is provided, it is applied to all tracers. Otherwise `κ` must be a `NamedTuple` with values for every tracer individually.

# Arguments

  * `time_discretization`: either `ExplicitTimeDiscretization()` (default) or `VerticallyImplicitTimeDiscretization()`.
  * `formulation`:

      * `HorizontalFormulation()` for diffusivity applied in the horizontal direction(s)
      * `VerticalFormulation()` for diffusivity applied in the vertical direction,
      * `ThreeDimensionalFormulation()` (default) for diffusivity applied isotropically to all directions
  * `FT`: the float datatype (default: `Float64`)

# Keyword arguments

  * `ν`: Viscosity. `Number`, `AbstractArray`, `Field`, or `Function`.
  * `κ`: Diffusivity. `Number`, `AbstractArray`, `Field`, `Function`, or      `NamedTuple` of diffusivities with entries for each tracer.
  * `discrete_form`: `Boolean`; default: `false`.

When prescribing the viscosities or diffusivities as functions, depending on the value of keyword argument `discrete_form`, the constructor expects:

  * `discrete_form = false` (default): functions of the grid's native coordinates and time, e.g., `(x, y, z, t)` for a `RectilinearGrid` or `(λ, φ, z, t)` for a `LatitudeLongitudeGrid`.
  * `discrete_form = true`:

      * with `loc = (nothing, nothing, nothing)` and `parameters = nothing` (default): functions of `(i, j, k, grid, ℓx, ℓy, ℓz, clock, fields)` with `ℓx`, `ℓy`, and `ℓz` either `Face()` or `Center()`.
      * with `loc = (ℓx, ℓy, ℓz)` with `ℓx`, `ℓy`, and `ℓz` either `Face()` or `Center()` and `parameters = nothing`: functions of `(i, j, k, grid, clock, fields)`.
      * with `loc = (nothing, nothing, nothing)` and specified `parameters`: functions of `(i, j, k, grid, ℓx, ℓy, ℓz, clock, fields, parameters)`.
      * with `loc = (ℓx, ℓy, ℓz)` and specified `parameters`: functions of `(i, j, k, grid, clock, fields, parameters)`.
  * `required_halo_size = 1`: the required halo size for the closure. This value should be an integer. change only if using a function for `ν` or `κ` that requires a halo size larger than 1 to compute.
  * `parameters`: `NamedTuple` with parameters used by the functions that compute viscosity and/or diffusivity; default: `nothing`.

# Examples

```jldoctest ScalarDiffusivity
julia> using Oceananigans

julia> ScalarDiffusivity(ν=1000, κ=2000)
ScalarDiffusivity{ExplicitTimeDiscretization}(ν=1000.0, κ=2000.0)
```

```jldoctest ScalarDiffusivity
julia> const depth_scale = 100;

julia> @inline ν(x, y, z, t) = 1000 * exp(z / depth_scale)
ν (generic function with 1 method)

julia> ScalarDiffusivity(ν=ν)
ScalarDiffusivity{ExplicitTimeDiscretization}(ν=ν (generic function with 1 method), κ=0.0)
```

```jldoctest ScalarDiffusivity
julia> using Oceananigans.Grids: znode

julia> @inline function κ(i, j, k, grid, ℓx, ℓy, ℓz, clock, fields)
           z = znode(i, j, k, grid, ℓx, ℓy, ℓz)
           return 2000 * exp(z / depth_scale)
       end
κ (generic function with 1 method)

julia> ScalarDiffusivity(κ=κ, discrete_form=true)
ScalarDiffusivity{ExplicitTimeDiscretization}(ν=0.0, κ=Oceananigans.TurbulenceClosures.DiscreteDiffusionFunction{Nothing, Nothing, Nothing, Nothing, typeof(κ)})
```

```jldoctest ScalarDiffusivity
julia> @inline function another_κ(i, j, k, grid, clock, fields, p)
           z = znode(i, j, k, grid, Center(), Center(), Face())
           return 2000 * exp(z / p.depth_scale)
       end
another_κ (generic function with 1 method)

julia> ScalarDiffusivity(κ=another_κ, discrete_form=true, loc=(Center, Center, Face), parameters=(; depth_scale = 120.0))
ScalarDiffusivity{ExplicitTimeDiscretization}(ν=0.0, κ=Oceananigans.TurbulenceClosures.DiscreteDiffusionFunction{Center, Center, Face, @NamedTuple{depth_scale::Float64}, typeof(another_κ)})
```
