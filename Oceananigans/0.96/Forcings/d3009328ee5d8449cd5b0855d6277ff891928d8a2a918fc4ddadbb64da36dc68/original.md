```
Relaxation(; rate, mask=onefunction, target=zerofunction)
```

Returns a `Forcing` that restores a field to `target(X..., t)` at the specified `rate`, in the region `mask(X...)`.

The functions `onefunction` and `zerofunction` always return 1 and 0, respectively. Thus the default `mask` leaves the whole domain uncovered, and the default `target` is zero.

# Example

  * Restore a field to zero on a timescale of "3600" (equal to one hour if the time units of the simulation are seconds).

```jldoctest relaxation
using Oceananigans

damping = Relaxation(rate = 1/3600)

# output
Relaxation{Float64, typeof(Oceananigans.Forcings.onefunction), typeof(Oceananigans.Forcings.zerofunction)}
├── rate: 0.0002777777777777778
├── mask: 1
└── target: 0
```

  * Restore a field to a linear z-gradient within the bottom 1/4 of a domain on a timescale of "60" (equal to one minute if the time units of the simulation are seconds).

```jldoctest relaxation
dTdz = 0.001 # ⁰C m⁻¹, temperature gradient

T₀ = 20 # ⁰C, surface temperature at z=0

Lz = 100 # m, depth of domain

bottom_sponge_layer = Relaxation(; rate = 1/60,
                                   target = LinearTarget{:z}(intercept=T₀, gradient=dTdz),
                                   mask = GaussianMask{:z}(center=-Lz, width=Lz/4))

# output
Relaxation{Float64, GaussianMask{:z, Float64}, LinearTarget{:z, Float64}}
├── rate: 0.016666666666666666
├── mask: exp(-(z + 100.0)^2 / (2 * 25.0^2))
└── target: 20.0 + 0.001 * z
```
