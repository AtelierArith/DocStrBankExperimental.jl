```
 SingleBendingPowerLaw(A, α₁, f₁, α₂)
```

Single bending power law model for the power spectral density

  * `A`: the amplitude
  * `α₁`: the first power law index
  * `f₁`: the first bend frequency
  * `α₂`: the second power law index

$$
\mathcal{P}(f) =  A \frac{(f/f₁)^{-α₁}}{1 + (f / f₁)^{α₂ - α₁}}
$$
