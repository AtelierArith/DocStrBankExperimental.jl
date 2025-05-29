```
TaylorFourierTransform.ar_phase(sol::TaylorFourierTransform.AbstractDTFTSolution, D::Int=0, H::Int=1)
```

Function to obtain the anti-rotating phase of the Dth-degree derivative of the  Hth-harmonic phasor.

```
∀ h ∈ {0}:
    φ₀⁽ᴰ⁾(t) = 0.0
∀ h ∉ {0}:
    φₕ⁽⁰⁾(t) = ∠[ψₕ⁽⁰⁾(t)] ∈ [-π,π]
    φₕ⁽¹⁾(t) = ℑ[2 ⋅ ψₕ⁽¹⁾(t) ⋅ exp(-im ⋅ φₕ⁽⁰⁾(t))] / aₕ⁽⁰⁾(t) ∈ 𝐑
    φₕ⁽²⁾(t) = {ℑ[2 ⋅ ψₕ⁽²⁾(t) ⋅ exp(-im ⋅ φₕ⁽⁰⁾(t))] - 2 ⋅ aₕ⁽¹⁾(t) ⋅ φₕ⁽¹⁾(t)} / aₕ⁽⁰⁾(t) ∈ 𝐑
```

See: [Assessing Synchrophasor Estimates of an Event Captured by a Phasor  Measurement Unit, pg. 3112](https://ieeexplore.ieee.org/document/9239915)

Input:

  * `sol::AbstractDTFTSolution`   | DTFT solution struct [-]
  * `D::Int`                      | degree of the derivative [-], default=0
  * `H::Int`                      | harmonic number [-], default=1

Output:

  * `φ::Vector{<:Real}`           | anti-rotating phase φₕ⁽ᴰ⁾(t) [(rad)]
