```
StokesDrift(; ∂z_uˢ=zerofunction, ∂y_uˢ=zerofunction, ∂t_uˢ=zerofunction,
              ∂z_vˢ=zerofunction, ∂x_vˢ=zerofunction, ∂t_vˢ=zerofunction,
              ∂x_wˢ=zerofunction, ∂y_wˢ=zerofunction, ∂t_wˢ=zerofunction, parameters=nothing)
```

Construct a set of functions of space and time for a Stokes drift velocity field corresponding to a surface gravity wave field with an envelope that (potentially) varies in the horizontal directions.

To resolve the evolution of the Lagrangian-mean momentum, we require all the components of the "psuedovorticity",

$$
𝛁 × 𝐯ˢ = \hat{\boldsymbol{x}} (∂_y wˢ - ∂_z vˢ) + \hat{\boldsymbol{y}} (∂_z uˢ - ∂_x wˢ) + \hat{\boldsymbol{z}} (∂_x vˢ - ∂_y uˢ)
$$

as well as the time-derivatives of $uˢ$, $vˢ$, and $wˢ$.

Note that each function (e.g., `∂z_uˢ`) is generally a function of depth, horizontal coordinates, and time.Thus, the correct function signature depends on the grid, since `Flat` horizontal directions are omitted.

For example, on a grid with `topology = (Periodic, Flat, Bounded)` (and `parameters=nothing`), then, e.g., `∂z_uˢ` is callable via `∂z_uˢ(x, z, t)`. When `!isnothing(parameters)`, then `∂z_uˢ` is callable via `∂z_uˢ(x, z, t, parameters)`. Similarly, on a grid with `topology = (Periodic, Periodic, Bounded)` and `parameters=nothing`, `∂z_uˢ` is called via `∂z_uˢ(x, y, z, t)`.

# Example

A wavepacket moving with the group velocity in the $x$-direction. We write the Stokes drift as:

$$
uˢ(x, y, z, t) = A(x - cᵍ \, t, y) ûˢ(z)
$$

with $A(ξ, η) = \exp{[-(ξ^2 + η^2) / 2δ^2]}$. We also assume $vˢ = 0$. If $𝐯ˢ$ represents the solenoidal component of the Stokes drift, then in this system from incompressibility requirement we have that $∂_z wˢ = - ∂_x uˢ = - (∂_ξ A) ûˢ$ and therefore, under the assumption that $wˢ$ tends to zero at large depths, we get $wˢ = - (∂_ξ A / 2k) ûˢ$.

```jldoctest
using Oceananigans
using Oceananigans.Units

g = 9.81 # gravitational acceleration

ϵ = 0.1
λ = 100meters  # horizontal wavelength
const k = 2π / λ  # horizontal wavenumber
c = sqrt(g / k)  # phase speed
const δ = 400kilometers  # wavepacket spread
const cᵍ = c / 2  # group speed
const Uˢ = ϵ^2 * c

@inline A(ξ, η) = exp(- (ξ^2 + η^2) / 2δ^2)

@inline ∂ξ_A(ξ, η) = - ξ / δ^2 * A(ξ, η)
@inline ∂η_A(ξ, η) = - η / δ^2 * A(ξ, η)
@inline ∂η_∂ξ_A(ξ, η) = η * ξ / δ^4 * A(ξ, η)
@inline ∂²ξ_A(ξ, η) = (ξ^2 / δ^2 - 1) * A(ξ, η) / δ^2

@inline ûˢ(z) = Uˢ * exp(2k * z)
@inline uˢ(x, y, z, t) = A(x - cᵍ * t, y) * ûˢ(z)

@inline ∂z_uˢ(x, y, z, t) = 2k * A(x - cᵍ * t, y) * ûˢ(z)
@inline ∂y_uˢ(x, y, z, t) = ∂η_A(x - cᵍ * t, y) * ûˢ(z)
@inline ∂t_uˢ(x, y, z, t) = - cᵍ * ∂ξ_A(x - cᵍ * t, y) * ûˢ(z)
@inline ∂x_wˢ(x, y, z, t) = - 1 / 2k * ∂²ξ_A(x - cᵍ * t, y) * ûˢ(z)
@inline ∂y_wˢ(x, y, z, t) = - 1 / 2k * ∂η_∂ξ_A(x - cᵍ * t, y) * ûˢ(z)
@inline ∂t_wˢ(x, y, z, t) = + cᵍ / 2k * ∂²ξ_A(x - cᵍ * t, y) * ûˢ(z)

stokes_drift = StokesDrift(; ∂z_uˢ, ∂t_uˢ, ∂y_uˢ, ∂t_wˢ, ∂x_wˢ, ∂y_wˢ)

# output

StokesDrift{Nothing}:
├── ∂x_vˢ: zerofunction
├── ∂x_wˢ: ∂x_wˢ
├── ∂y_uˢ: ∂y_uˢ
├── ∂y_wˢ: ∂y_wˢ
├── ∂z_uˢ: ∂z_uˢ
├── ∂z_vˢ: zerofunction
├── ∂t_uˢ: ∂t_uˢ
├── ∂t_vˢ: zerofunction
└── ∂t_wˢ: ∂t_wˢ
```
