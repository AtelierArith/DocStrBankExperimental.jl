```julia
VorticityTensorModulus(model; location)

```

Calculate the modulus (absolute value) of the vorticity tensor `Ω`, which is defined as the antisymmetric part of the velocity gradient tensor:

```
    Ωᵢⱼ = ½(∂ⱼuᵢ - ∂ᵢuⱼ)
```

Its modulus is then defined (using Einstein summation notation) as

```
    || Ωᵢⱼ || = √(Ωᵢⱼ Ωᵢⱼ)
```
