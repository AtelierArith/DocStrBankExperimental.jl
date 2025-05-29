```julia
SlashedGaussianRing(σ, s)

```

Implements the slashed gaussian ring template, that uses a cosine to implement the slash and has a brightness position angle of 0 degrees east of north.

## Arguments

  * `σ` : standard deviation of the Gaussian ring
  * `s` : Slash amplitude. 0 means no slash, and 1 is maximal.

## Notes

This is a convienence constructor that uses [`RingTemplate`](@ref) under the hood. To create this function your self do

```julia
RingTemplate(RadialGaussian(σ), AzimuthalCosine((s,), (zero(s),)))
```
