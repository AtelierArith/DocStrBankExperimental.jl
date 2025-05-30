```
Emission  <: AbstractEmission
```

Type Emission contains the coefficients for (convective) heat transfer and heat radiation 

$$
\Phi = -h ~ (\theta - \theta_{amb}) - \sigma ~ [\varepsilon_{1} ~ \theta^4 - \varepsilon_{2} ~ \theta_{amb}^4)]
$$

Constructor `Emission(h, θamb, ε₁, ε₂, θext)` expects emissivity `ε₁` and `ε₂` which must be in interval [0,1]. The Stefan-Boltzmann constant is stored internally: `σ = 5.6703744191844294e-8`.

### Elements

`h` : heat transfer coefficient

`θamb` : ambient temperature

`ε₁` : Emissivity of main object

`ε₂` : Emissivity of external second body

`θext` : temperature of an external second body
