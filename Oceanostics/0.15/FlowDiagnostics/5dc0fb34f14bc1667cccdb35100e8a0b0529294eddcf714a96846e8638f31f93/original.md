```julia
StrainRateTensorModulus(model; location)

```

Calculate the modulus (absolute value) of the strain rate tensor `S`, which is defined as the symmetric part of the velocity gradient tensor:

```
    Sᵢⱼ = ½(∂ⱼuᵢ + ∂ᵢuⱼ)
```

Its modulus is then defined (using Einstein summation notation) as

```
    || Sᵢⱼ || = √(Sᵢⱼ Sᵢⱼ)
```
