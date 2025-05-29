```
Rotate(γ)
Rotate(distribution)
Rotate(α, β, γ)
Rotate(α_distribution, β_distribution, γ_distribution)
```

Rotate spatial data around its center. Rotate(γ) is a 2D rotation by an angle chosen uniformly from [-γ, γ], an angle given in degrees. Rotate(α, β, γ) is a 3D rotation by angles chosen uniformly from [-α, α], [-β, β], and [-γ, γ], for X, Y, and Z rotations.

You can also pass any `Distributions.Sampleable` from which the angle is selected.

## Examples

```julia
tfm2d = Rotate(10)
apply(tfm2d, Image(rand(Float32, 16, 16)))

tfm3d = Rotate(10, 20, 30)
apply(tfm3d, Image(rand(Float32, 16, 16, 16)))
```
