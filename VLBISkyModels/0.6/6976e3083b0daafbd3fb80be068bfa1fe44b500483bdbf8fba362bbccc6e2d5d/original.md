```julia
GaussianRing(σ)

```

Implements the gaussian ring template.

## Notes

This is a convienence constructor that uses [`RingTemplate`](@ref) under the hood. To create this function your self do

```julia
RingTemplate(RadialGaussian(σ), AzimuthalUniform())
```

## Arguments

  * `σ` : standard deviation of the Gaussian ring
