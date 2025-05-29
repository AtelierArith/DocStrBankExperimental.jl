```
SIA2Dmodel(
    params::Sleipnir.Parameters;
    A::Union{R, Nothing} = nothing,
    n::Union{R, Nothing} = nothing,
    C::Union{R, Matrix{R}, Nothing} = nothing,
    H₀::Matrix{R} = Matrix{Sleipnir.Float}([;;]),
    H::Union{Matrix{R}, Nothing} = nothing,
    H̄::Union{Matrix{R}, Nothing} = nothing,
    S::Matrix{R} = Matrix{Sleipnir.Float}([;;]),
    dSdx::Union{Matrix{R}, Nothing} = nothing,
    dSdy::Union{Matrix{R}, Nothing} = nothing,
    D::Union{Matrix{R}, Nothing} = nothing,
    D_is_provided::Union{Bool, Nothing} = nothing,
    Dx::Union{Matrix{R}, Nothing} = nothing,
    Dy::Union{Matrix{R}, Nothing} = nothing,
    dSdx_edges::Union{Matrix{R}, Nothing} = nothing,
    dSdy_edges::Union{Matrix{R}, Nothing} = nothing,
    ∇S::Union{Matrix{R}, Nothing} = nothing,
    ∇Sy::Union{Matrix{R}, Nothing} = nothing,
    ∇Sx::Union{Matrix{R}, Nothing} = nothing,
    Fx::Union{Matrix{R}, Nothing} = nothing,
    Fy::Union{Matrix{R}, Nothing} = nothing,
    Fxx::Union{Matrix{R}, Nothing} = nothing,
    Fyy::Union{Matrix{R}, Nothing} = nothing,
    V::Union{Matrix{R}, Nothing} = nothing,
    Vx::Union{Matrix{R}, Nothing} = nothing,
    Vy::Union{Matrix{R}, Nothing} = nothing,
    Γ::Union{R, Nothing} = nothing,
    MB::Union{Matrix{R}, Nothing} = nothing,
    MB_mask::Union{BitMatrix, Nothing} = nothing,
    MB_total::Union{Matrix{R}, Nothing} = nothing,
    glacier_idx::Union{I, Nothing} = nothing
) where {I <: Integer, R <: Real}
```

Constructs a new `SIA2Dmodel` object with the given parameters.

# Arguments

  * `params::Sleipnir.Parameters`: Simulation parameters.
  * `A::Union{R, Nothing}`: Flow law parameter (default: `nothing`).
  * `n::Union{R, Nothing}`: Flow law exponent (default: `nothing`).
  * `C::Union{R, Matrix{R}, Nothing}`: Basal sliding parameter (default: `nothing`).
  * `H₀::Matrix{R}`: Initial ice thickness (default: empty matrix).
  * `H::Union{Matrix{R}, Nothing}`: Ice thickness (default: `nothing`).
  * `H̄::Union{Matrix{R}, Nothing}`: Averaged ice thickness (default: `nothing`).
  * `S::Matrix{R}`: Surface elevation (default: empty matrix).
  * `dSdx::Union{Matrix{R}, Nothing}`: Surface slope in x-direction (default: `nothing`).
  * `dSdy::Union{Matrix{R}, Nothing}`: Surface slope in y-direction (default: `nothing`).
  * `D::Union{Matrix{R}, Nothing}`: Diffusivity (default: `nothing`).
  * `D_is_provided::Union{Bool, Nothing}`: Specifies if D is provided by user or computed (default: `false`).
  * `Dx::Union{Matrix{R}, Nothing}`: Diffusivity in x-direction (default: `nothing`).
  * `Dy::Union{Matrix{R}, Nothing}`: Diffusivity in y-direction (default: `nothing`).
  * `dSdx_edges::Union{Matrix{R}, Nothing}`: Surface slope at edges in x-direction (default: `nothing`).
  * `dSdy_edges::Union{Matrix{R}, Nothing}`: Surface slope at edges in y-direction (default: `nothing`).
  * `∇S::Union{Matrix{R}, Nothing}`: Gradient of surface elevation (default: `nothing`).
  * `∇Sy::Union{Matrix{R}, Nothing}`: Gradient of surface elevation in y-direction (default: `nothing`).
  * `∇Sx::Union{Matrix{R}, Nothing}`: Gradient of surface elevation in x-direction (default: `nothing`).
  * `Fx::Union{Matrix{R}, Nothing}`: Flux in x-direction (default: `nothing`).
  * `Fy::Union{Matrix{R}, Nothing}`: Flux in y-direction (default: `nothing`).
  * `Fxx::Union{Matrix{R}, Nothing}`: Second derivative of flux in x-direction (default: `nothing`).
  * `Fyy::Union{Matrix{R}, Nothing}`: Second derivative of flux in y-direction (default: `nothing`).
  * `V::Union{Matrix{R}, Nothing}`: Velocity (default: `nothing`).
  * `Vx::Union{Matrix{R}, Nothing}`: Velocity in x-direction (default: `nothing`).
  * `Vy::Union{Matrix{R}, Nothing}`: Velocity in y-direction (default: `nothing`).
  * `Γ::Union{R, Nothing}`: Auxiliary matrix (default: `nothing`).
  * `MB::Union{Matrix{R}, Nothing}`: Mass balance (default: `nothing`).
  * `MB_mask::Union{BitMatrix, Nothing}`: Mask for mass balance (default: `nothing`).
  * `MB_total::Union{Matrix{R}, Nothing}`: Total mass balance (default: `nothing`).
  * `glacier_idx::Union{I, Nothing}`: Index of the glacier (default: `nothing`).

# Returns

  * `SIA2Dmodel`: A new `SIA2Dmodel` object.
