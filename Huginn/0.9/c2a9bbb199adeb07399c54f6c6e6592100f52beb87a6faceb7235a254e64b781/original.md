```
mutable struct SIA2Dmodel{R <: Real, I <: Integer} <: SIAmodel
```

A mutable struct representing a 2D Shallow Ice Approximation (SIA) model.

# Fields

  * `A::Union{Ref{R}, Nothing}`: Flow rate factor.
  * `n::Union{Ref{R}, Nothing}`: Flow law exponent.
  * `C::Union{Ref{R}, Matrix{R}, Nothing}`: Sliding coefficient.
  * `H₀::Matrix{R}`: Initial ice thickness.
  * `H::Union{Matrix{R}, Nothing}`: Ice thickness.
  * `H̄::Union{Matrix{R}, Nothing}`: Averaged ice thickness.
  * `S::Matrix{R}`: Surface elevation.
  * `dSdx::Union{Matrix{R}, Nothing}`: Surface slope in the x-direction.
  * `dSdy::Union{Matrix{R}, Nothing}`: Surface slope in the y-direction.
  * `D::Union{Matrix{R}, Nothing}`: Diffusivity.
  * `D_is_provided::Union{Bool, Nothing}`: Specifies if D is provided by user or computed.
  * `Dx::Union{Matrix{R}, Nothing}`: Diffusivity in the x-direction.
  * `Dy::Union{Matrix{R}, Nothing}`: Diffusivity in the y-direction.
  * `dSdx_edges::Union{Matrix{R}, Nothing}`: Surface slope at edges in the x-direction.
  * `dSdy_edges::Union{Matrix{R}, Nothing}`: Surface slope at edges in the y-direction.
  * `∇S::Union{Matrix{R}, Nothing}`: Gradient of the surface elevation.
  * `∇Sy::Union{Matrix{R}, Nothing}`: Gradient of the surface elevation in the y-direction.
  * `∇Sx::Union{Matrix{R}, Nothing}`: Gradient of the surface elevation in the x-direction.
  * `Fx::Union{Matrix{R}, Nothing}`: Flux in the x-direction.
  * `Fy::Union{Matrix{R}, Nothing}`: Flux in the y-direction.
  * `Fxx::Union{Matrix{R}, Nothing}`: Second derivative of flux in the x-direction.
  * `Fyy::Union{Matrix{R}, Nothing}`: Second derivative of flux in the y-direction.
  * `V::Union{Matrix{R}, Nothing}`: Velocity.
  * `Vx::Union{Matrix{R}, Nothing}`: Velocity in the x-direction.
  * `Vy::Union{Matrix{R}, Nothing}`: Velocity in the y-direction.
  * `Γ::Union{Ref{R}, Nothing}`: Basal shear stress.
  * `MB::Union{Matrix{R}, Nothing}`: Mass balance.
  * `MB_mask::Union{AbstractArray{Bool}, Nothing}`: Mask for mass balance.
  * `MB_total::Union{Matrix{R}, Nothing}`: Total mass balance.
  * `glacier_idx::Union{Ref{I}, Nothing}`: Index of the glacier.
