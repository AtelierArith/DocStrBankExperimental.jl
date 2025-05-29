```julia
SlashedGaussianRing(r0, σ, s, ξ, x0, y0)

```

Implements the slashed gaussian ring template, that uses a cosine to implement the slash.

## Arguments

  * `r0`: radius of the ring
  * `σ` : standard deviation of the Gaussian ring
  * `s` : Slash amplitude. 0 means no slash, and 1 is maximal.
  * `ξs`: azimuthal peak brightness P.A. measured east of north
  * `x0`: location of the ring center horizontally
  * `y0`: location of the ring center vertically

## Notes

This is a convienence constructor that uses [`RingTemplate`](@ref) under the hood. To create this function your self do

```julia
modify(SlashedGaussianRing(σ/r0, s), Stretch(r0), Rotate(ξ), Shift(x0, y0))
```
