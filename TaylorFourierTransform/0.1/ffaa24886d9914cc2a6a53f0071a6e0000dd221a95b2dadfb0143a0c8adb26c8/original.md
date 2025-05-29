```
TaylorFourierTransform.frequency(sol::TaylorFourierTransform.AbstractDTFTSolution, H::Int=1)
```

Function to obtain the frequency of the zeroth-degree derivative of the  Hth-harmonic phasor.

```
fₕ(t) = Fₕ + ϕₕ⁽¹⁾(t) / (2 π) ∈ 𝐑⁺
```

See: [Fast Taylor-Fourier Transform for Monitoring Modern Power Grids with  Real-Time Dynamic Harmonic Estimation](tbp)

Input:

  * `sol::AbstractDTFTSolution`   | DTFT solution struct [-]
  * `H::Int`                      | harmonic number [-], default=1

Output:

  * `f::Vector{<:Real}`           | frequency fₕ(t) [Hz]
