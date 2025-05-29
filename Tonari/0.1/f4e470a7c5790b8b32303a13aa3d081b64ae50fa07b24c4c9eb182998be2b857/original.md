```
 DoubleBendingPowerLaw(α₁, f₁, α₂, f₂, α₃)
```

Double bending power law model for the power spectral density

  * `α₁`: the first power law index
  * `f₁`: the first bend frequency
  * `α₂`: the second power law index
  * `f₂`: the second bend frequency
  * `α₃`: the third power law index

$$
\mathcal{P}(f) =  A\frac{(f/f₁)^{-α₁}}{1 + (f / f₁)^{α₂ - α₁}}\frac{1}{1 + (f / f₂)^{α₃ - α₂}}
$$
