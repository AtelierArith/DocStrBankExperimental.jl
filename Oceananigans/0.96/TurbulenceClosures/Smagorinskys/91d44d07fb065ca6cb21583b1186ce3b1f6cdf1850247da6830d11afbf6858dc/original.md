```
LillyCoefficient([FT=Float64;] smagorinsky=0.16, reduction_factor=1)
```

When used with `Smagorinsky`, it calculates the Smagorinsky coefficient according to closure proposed by [Lilly62](@citet), and [Lilly66](@citet), which has an eddy viscosity of the form

```
νₑ = (Cˢ * Δᶠ)² * √(2Σ²) * √(1 - Cb * N² / Σ²)
```

where `C²` is the Smagorinsky coefficient, `Δᶠ` is the filter width, `Σ² = ΣᵢⱼΣᵢⱼ` is the double dot product of the strain tensor `Σᵢⱼ`, `N²` is the total buoyancy gradient, and `Cb` is a constant the multiplies the Richardson number modification to the eddy viscosity.

# Arguments

  * `FT`: Float type; default `Float64`.

# Keyword arguments

  * `smagorinsky`: Smagorinsky coefficient `Cˢ`. Default value is 0.16 as obtained by Lilly (1966).
  * `reduction_factor`: Buoyancy term multipler `Cb` based on Lilly (1962) (`reduction_factor = 0`       turns it off, `reduction_factor ≠ 0` turns it on.       Typically, and according to the original work by Lilly (1962), `Cb = 1 / Pr`.)

# References

Lilly, D. K. "On the numerical simulation of buoyant convection." Tellus (1962)

Lilly, D. K. "The representation of small-scale turbulence in numerical simulation experiments."     NCAR Manuscript No. 281, 0, (1966)
