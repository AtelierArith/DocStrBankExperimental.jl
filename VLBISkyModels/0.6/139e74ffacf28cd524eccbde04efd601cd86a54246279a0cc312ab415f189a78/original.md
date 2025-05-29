```julia
GaussianRing(r0, σ, x0, y0)

```

Implements the gaussian ring template.

## Notes

This is a convienence constructor that uses [`RingTemplate`](@ref) under the hood. To create this function your self do

```julia
modify(GaussianRing(σ/r0), Stretch(r0), Shift(x0, y0))
```

## Arguments

  * `r0`: radius of the ring
  * `σ` : standard deviation of the Gaussian ring
  * `x0`: location of the ring center horizontally
  * `y0`: location of the ring center vertically
