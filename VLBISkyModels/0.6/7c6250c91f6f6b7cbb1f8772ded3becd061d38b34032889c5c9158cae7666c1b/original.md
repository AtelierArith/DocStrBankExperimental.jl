```julia
EllipticalGaussianRing(r0, σ, τ, ξτ, x0, y0)

```

Implements the elliptical gaussian ring template with semi-minor axis `a` and semi-major axis `b`.

## Arguments

  * `r0`: geometric mean radius (√ab) of the ring
  * `σ` : standard deviation of the Gaussian ring
  * `τ` : asymmetry of the ring τ = 1-b/a
  * `ξτ`: semi-major axis measured east of north
  * `x0`: location of the ring center horizontally
  * `y0`: location of the ring center vertically

## Notes

This is a convienence constructor that uses [`RingTemplate`](@ref) under  the hood. To create this function your self do

`julia  modify(GaussianRing(σ/r0), Stretch(r0*sqrt(1-τ), r0/sqrt(1-τ)), Rotate(ξτ), Shift(x0, y0))`
