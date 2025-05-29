```
κ² = coherence(d; n = length(d)÷10, noverlap = n÷2, window=hamming, method=:welch)
```

Calculates the magnitude-squared coherence Function. κ² close to 1 indicates a good explainability of energy in the output signal by energy in the input signal. κ² << 1 indicates that either the system is nonlinear, or a strong noise contributes to the output energy.

  * κ: Squared coherence function in the form of an [`FRD`](@ref).
  * `method`: `:welch` or `:corr`. `:welch` uses the Welch method to estimate the power spectral density, while `:corr` uses the Correlogram approach . For `method = :corr`, the additional keyword argument `σ` determines the width of the Gaussian window applied to the estimated correlation functions before FFT. A larger `σ` implies less smoothing.

See also [`coherenceplot`](@ref)

# Extended help:

For the signal model $y = Gu + v$, $κ²$ is defined as 

$$
κ(ω)^2 = \dfrac{S_{uy}}{S_{uu} S_{yy}} = \dfrac{|G(iω)|^2S_{uu}^2}{S_{uu} (|G(iω)|^2S_{uu}^2 + S_{vv})} = \dfrac{1}{1 + \dfrac{S_{vv}}{S_{uu}|G(iω)|^2}}
$$

from which it is obvious that $0 ≤ κ² ≤ 1$ and that κ² is close to 1 if the noise energy $S_{vv}$ is small compared to the output energy due to the input $S_{uu}|G(iω)|^2$.
