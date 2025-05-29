```julia
QVelocityGradientTensorInvariant(model; location)

```

Calculate the value of the `Q` velocity gradient tensor invariant. This is usually just called `Q` and it is generally used for identifying and visualizing vortices in fluid flow.

The definition and nomenclature comes from the equation for the eigenvalues `λ` of the velocity gradient tensor `∂ⱼuᵢ`:

```
    λ³ + P λ² + Q λ + T = 0
```

from where `Q` is defined as

```
    Q = ½ (ΩᵢⱼΩᵢⱼ - SᵢⱼSᵢⱼ)
```

and where `Sᵢⱼ= ½(∂ⱼuᵢ + ∂ᵢuⱼ)` and `Ωᵢⱼ= ½(∂ⱼuᵢ - ∂ᵢuⱼ)`. More info about it can be found in doi:10.1063/1.5124245.
