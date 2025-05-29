```
VectorInvariant(; vorticity_scheme = EnstrophyConserving(),
                  vorticity_stencil = VelocityStencil(),
                  vertical_scheme = EnergyConserving(),
                  divergence_scheme = vertical_scheme,
                  kinetic_energy_gradient_scheme = divergence_scheme,
                  upwinding  = OnlySelfUpwinding(; cross_scheme = divergence_scheme),
                  multi_dimensional_stencil = false)
```

Return a vector-invariant momentum advection scheme.

# Keyword arguments

  * `vorticity_scheme`: Scheme used for `Center` reconstruction of vorticity. Default: `EnstrophyConserving()`. Options:

      * `UpwindBiased()`
      * `WENO()`
      * `EnergyConserving()`
      * `EnstrophyConserving()`
  * `vorticity_stencil`: Stencil used for smoothness indicators for `WENO` schemes. Default: `VelocityStencil()`. Options:

      * `VelocityStencil()` (smoothness based on horizontal velocities)
      * `DefaultStencil()` (smoothness based on variable being reconstructed)
  * `vertical_scheme`: Scheme used for vertical advection of horizontal momentum. Default: `EnergyConserving()`.
  * `kinetic_energy_gradient_scheme`: Scheme used for kinetic energy gradient reconstruction. Default: `vertical_scheme`.
  * `divergence_scheme`: Scheme used for divergence flux. Only upwinding schemes are supported. Default: `vorticity_scheme`.
  * `upwinding`: Treatment of upwinded reconstruction of divergence and kinetic energy gradient. Default: `OnlySelfUpwinding()`. Options:

      * `CrossAndSelfUpwinding()`
      * `OnlySelfUpwinding()`
  * `multi_dimensional_stencil`: whether or not to use a horizontal two-dimensional stencil for the reconstruction                              of vorticity, divergence and kinetic energy gradient. Currently the "tangential"                              direction uses 5th-order centered WENO reconstruction. Default: false

# Examples

```jldoctest
julia> using Oceananigans

julia> VectorInvariant()
Vector Invariant, Dimension-by-dimension reconstruction
 Vorticity flux scheme:
 └── Oceananigans.Advection.EnstrophyConserving{Float64}
 Vertical advection / Divergence flux scheme:
 └── Oceananigans.Advection.EnergyConserving{Float64}
```

```jldoctest
julia> using Oceananigans

julia> VectorInvariant(vorticity_scheme = WENO(), vertical_scheme = WENO(order = 3))
Vector Invariant, Dimension-by-dimension reconstruction
 Vorticity flux scheme:
 ├── WENO(order=5)
 └── smoothness ζ: Oceananigans.Advection.VelocityStencil()
 Vertical advection / Divergence flux scheme:
 ├── WENO(order=3)
 └── upwinding treatment: OnlySelfUpwinding
 KE gradient and Divergence flux cross terms reconstruction:
 └── Centered(order=2)
 Smoothness measures:
 ├── smoothness δU: FunctionStencil f = divergence_smoothness
 ├── smoothness δV: FunctionStencil f = divergence_smoothness
 ├── smoothness δu²: FunctionStencil f = u_smoothness
 └── smoothness δv²: FunctionStencil f = v_smoothness
```
