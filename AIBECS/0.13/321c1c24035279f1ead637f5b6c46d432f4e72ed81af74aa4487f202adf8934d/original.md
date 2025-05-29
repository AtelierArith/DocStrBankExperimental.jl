```
PFDO(grd; w_top)
```

Builds the particle-flux-divergence operator `PFDO` for a given particle sinking speed (`w_top`).

Schematic of a grid cell:

```
     top  ┌─────────────────────────────────┐   ┬
          │      ↓ w_top          ↓ Φ_top   │   │
          │ (settling velovity)    (flux)   │   │
          │                                 │   │
          │            x                    │   δz
          │      (particle conc.)           │   │
          │                                 │   │
          │                                 │   │
  bottom  └─────────────────────────────────┘   ┴
```

  * `δz` is the height of grid cell [m]
  * `w_top` is the particle sinking speed at the top of the grid cell [m s⁻¹]
  * `Φ_top` is the flux at the top of the grid cell [mol m⁻² s⁻¹]
  * `x` is the particle concentration of the cell [mol m⁻³]

The PFDO is defined by

```
PFDO * x = δΦ/δz ≈ dΦ/dz,
```

i.e., so that applied to `x` it approximates the flux divergence of `x`, dΦ/δz. It is calculated as the matrix product of DIVO and FATO:

```
PFDO = DIVO * FATO.
```

where the divergence operator `DIVO`, is defined by (`z` increasing downward)

```
DIVO * ϕ_top = 1/δz * (ϕ_top[below] - ϕ_top) = δϕ/δz ≈ dΦ/δz.
```

and FATO, the flux-at-top operator, is defined by

```
FATO * x = w_top * x[above] ≈ ϕ_top.
```

# Example

```julia-repl
julia> PFDO(grd, w_top=1.0) # 1.0 m/s (SI units assumed)
```
