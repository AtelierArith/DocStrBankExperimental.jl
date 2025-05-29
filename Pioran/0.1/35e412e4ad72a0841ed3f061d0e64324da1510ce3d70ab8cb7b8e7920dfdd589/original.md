```
 DoubleBendingPowerLaw_Bis(α₀, f₁, Δα₁, Δf, Δα₂)

Double bending power law model for the power spectral density
```

  * `α₀`: the first power law index
  * `f₁`: the first bend frequency
  * `Δα₁`: the first difference in power law index
  * `Δf`: scale for the second bend frequency, `f₂ = f₁ * Δf`
  * `Δα₂`: the second difference in power law index

$$
\mathcal{P}(f) =  \frac{(f/f₁)^{-α_0}}{1 + (f / f₁)^{α_0+\Delta α₁}}\frac{1}{1 + (f / f₁ \Delta f)^{\Delta α₁ + \Delta α₂}}
$$
