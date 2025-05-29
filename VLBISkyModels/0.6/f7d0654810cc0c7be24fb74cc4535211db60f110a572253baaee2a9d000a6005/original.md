```julia
CosineRingwGFloor(r0, σ0, σ, ξσ, s, ξs, floor, σG, x0, y0)

```

A Cosine ring with a Gaussian blob at the center of the ring. This is a convienence constructor of the more basic VLBISkyModel image constructors. It is equivalent to

```julia-repl
julia> CosineRing(r0, σ0, σ, ξσ, s, ξs, x0, y0) + floor*modify(Gaussian(), Stretch(σG), Shift(x0, y0))
```

### Details

Adds ellipticity to the ring. The radius `r0` of the ring is now defined as the geometric mean of the semi-major (a) and semi-minor (b) axis lengths i.e.

r0 = √(a*b).

The ellipticity `τ` is given by τ = 1-b/a.

## Arguments

  * `r0`: geometric mean radius (√ab) of the ring
  * `σ0`: standard deviation of the Gaussian ring
  * `σ` : amplitudes of the `N` order cosine expansion of the ring thickness
  * `ξσ`: phase of the `N` order cosine expansion of the ring thickness
  * `s` : amplitudes of the `M` order cosine expansion of the azimuthal brightness
  * `ξs`: phase of the `M` order cosine expansion of the azimuthal brightness
  * `floor`: The flux of the center Gaussian. This is relative to the CosineRing.
  * `σG`: The size of the central Gaussian.
  * `x0`: location of the ring center horizontally
  * `y0`: location of the ring center vertically
