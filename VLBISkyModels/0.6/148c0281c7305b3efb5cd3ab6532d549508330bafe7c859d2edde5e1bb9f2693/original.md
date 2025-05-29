```julia
EllipticalSlashedGaussianRing(r0, σ, τ, ξτ, s, ξs, x0, y0)

```

Combination of the elliptical and slashed gaussian ring.

### Details

Adds ellipticity to the ring. The radius `r0` of the ring is now defined as the geometric mean of the semi-major (a) and semi-minor (b) axis lengths i.e.

r0 = √(a*b).

The ellipticity `τ` is given by τ = 1-b/a.

The brightness asymmetry uses a cosine to implement the slash.

## Arguments

  * `r0`: geometric mean radius (√ab) of the Gaussian ring
  * `σ` : standard deviation of the Gaussian ring
  * `τ` : asymmetry of the Gaussian ring τ = 1-b/a
  * `ξτ`: semi-major axis measured east of north
  * `s` : Slash amplitude. 0 means no slash, and 1 is maximal.
  * `ξs`: azimuthal peak brightness P.A. measured east of north
  * `x0`: location of the ring center horizontally
  * `y0`: location of the ring center vertically

## Notes

This is a convienence constructor that uses [`RingTemplate`](@ref) under  the hood. To create this function your self we define

`julia  modify(SlashedGaussianRing(σ/r0, s),             Rotate(ξs-ξτ),             Stretch(r0*sqrt(1-τ), r0/sqrt(1-τ)),             Rotate(ξτ),             Shift(x0, y0)         )`
