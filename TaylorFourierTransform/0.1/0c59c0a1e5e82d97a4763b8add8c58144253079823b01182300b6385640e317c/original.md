```
TaylorFourierTransform.rocof(sol::TaylorFourierTransform.AbstractDTFTSolution, H::Int=1)
```

Function to obtain the rate-of-change-of-frequency of the zeroth-degree  derivative of the Hth-harmonic phasor.

```
rₕ(t) = ϕₕ⁽²⁾(t) / (2 π)² ∈ 𝐑
```

See: [Fast Taylor-Fourier Transform for Monitoring Modern Power Grids with  Real-Time Dynamic Harmonic Estimation](tbp)

Input:

  * `sol::AbstractDTFTSolution`   | DTFT solution struct [-]
  * `H::Int`                      | harmonic number [-], default=1

Output:

  * `r::Vector{<:Real}`           | rocof rₕ(t) [Hz²]
