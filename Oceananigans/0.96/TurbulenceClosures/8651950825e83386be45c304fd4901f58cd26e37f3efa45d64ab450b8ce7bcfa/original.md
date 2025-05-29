```
ScalarBiharmonicDiffusivity(formulation = ThreeDimensionalFormulation(), FT = Float64;
                            ν = 0,
                            κ = 0,
                            discrete_form = false,
                            loc = (nothing, nothing, nothing),
                            parameters = nothing)
```

Return a scalar biharmonic diffusivity turbulence closure with viscosity coefficient `ν` and tracer diffusivities `κ` for each tracer field in `tracers`. If a single `κ` is provided, it is applied to all tracers. Otherwise `κ` must be a `NamedTuple` with values for every tracer individually.

# Arguments

  * `formulation`:

      * `HorizontalFormulation()` for diffusivity applied in the horizontal direction(s)
      * `VerticalFormulation()` for diffusivity applied in the vertical direction,
      * `ThreeDimensionalFormulation()` (default) for diffusivity applied isotropically to all directions
  * `FT`: the float datatype (default: `Float64`)

# Keyword arguments

  * `ν`: Viscosity. `Number`, `AbstractArray`, `Field`, or `Function`.
  * `κ`: Diffusivity. `Number`, `AbstractArray`, `Field`, `Function`, or      `NamedTuple` of diffusivities with entries for each tracer.
  * `discrete_form`: `Boolean`; default: `false`.
  * `required_halo_size = 2`: the required halo size for the closure. This value should be an integer. change only if using a function for `ν` or `κ` that requires a halo size larger than 1 to compute.

When prescribing the viscosities or diffusivities as functions, depending on the value of keyword argument `discrete_form`, the constructor expects:

  * `discrete_form = false` (default): functions of the grid's native coordinates and time, e.g., `(x, y, z, t)` for a `RectilinearGrid` or `(λ, φ, z, t)` for a `LatitudeLongitudeGrid`.
  * `discrete_form = true`:

      * with `loc = (nothing, nothing, nothing)` (default): functions of `(i, j, k, grid, ℓx, ℓy, ℓz)` with `ℓx`, `ℓy`, and `ℓz` either `Face()` or `Center()`.
      * with `loc = (ℓx, ℓy, ℓz)` with `ℓx`, `ℓy`, and `ℓz` either `Face()` or `Center()`: functions of `(i, j, k, grid)`.
  * `parameters`: `NamedTuple` with parameters used by the functions that compute viscosity and/or diffusivity; default: `nothing`.

For examples see [`ScalarDiffusivity`](@ref).
