```
TaylorFourierTransform.phase(sol::TaylorFourierTransform.AbstractDTFTSolution, D::Int=0, H::Int=1)
```

Function to obtain the alternative angle of the Dth-degree derivative of the  Hth-harmonic phasor.

```
∀ h ∈ {0}:
    ϕ₀⁽ᴰ⁾(t) = 0.0
∀ h ∉ {0}:
    ϕₕ⁽⁰⁾(t) = ∠[pₕ⁽⁰⁾(t)] ∈ [-π,π]
    ϕₕ⁽¹⁾(t) = ℑ[2 ⋅ ξₕ⁽¹⁾(t) ⋅ exp(-im ⋅ ϕₕ⁽⁰⁾(t))] / aₕ⁽⁰⁾(t) ∈ 𝐑
    ϕₕ⁽²⁾(t) = {ℑ[2 ⋅ ξₕ⁽²⁾(t) ⋅ exp(-im ⋅ ϕₕ⁽⁰⁾(t))] - 2 ⋅ aₕ⁽¹⁾(t) ⋅ ϕₕ⁽¹⁾(t)} / aₕ⁽⁰⁾(t) ∈ 𝐑
```

See: [Assessing Synchrophasor Estimates of an Event Captured by a Phasor  Measurement Unit, pg. 3112](https://ieeexplore.ieee.org/document/9239915)

Input:

  * `sol::AbstractDTFTSolution`   | DTFT solution struct [-]
  * `D::Int`                      | degree of the derivative [-], default=0
  * `H::Int`                      | harmonic number [-], default=1

Output:

  * `ϕ::Vector{<:Real}`           | phase ϕₕ⁽ᴰ⁾(t) [(rad)]
