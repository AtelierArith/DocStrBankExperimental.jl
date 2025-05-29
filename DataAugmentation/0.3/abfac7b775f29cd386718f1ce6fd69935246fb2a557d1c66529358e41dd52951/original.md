```
Reflect(γ)
Reflect(distribution)
```

Reflect 2D spatial data around the center by an angle chosen at uniformly from [-γ, γ], an angle given in degrees.

You can also pass any `Distributions.Sampleable` from which the angle is selected.

## Examples

```julia
tfm = Reflect(10)
```
