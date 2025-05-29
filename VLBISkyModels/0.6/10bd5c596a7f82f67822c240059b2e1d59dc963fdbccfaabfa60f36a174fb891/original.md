```julia
EllipticalCosineRing(r0, σ0, σ, ξσ, τ, ξτ, s, ξs, x0, y0)

```

An Elliptical Cosine ring. This is a convienence constructor of the more basic VLBISkyModel image constructors. It is equivalent to

```julia-repl
julia> modify(CosineRing(σ0/r0, σ/r0, ξσ, s, ξs .- ξτ),
            Stretch(r0*sqrt(1-τ), r0/sqrt(1-τ)),
            Rotate(ξτ),
            Shift(x0, y0)
        )
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
  * `τ` : asymmetry of the ring τ = 1-b/a
  * `ξτ`: semi-major axis measured east of north
  * `s` : amplitudes of the `M` order cosine expansion of the azimuthal brightness
  * `ξs`: phase of the `M` order cosine expansion of the azimuthal brightness
  * `x0`: horizontal location of the ring center
  * `y0`: vertical location of the ring center vertically
