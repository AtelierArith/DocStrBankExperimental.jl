```
TaylorFourierTransform.amplitude(sol::TaylorFourierTransform.AbstractDTFTSolution, D::Int=0, H::Int=1)
```

Function to obtain the amplitude of the Dth-degree derivative of the  Hth-harmonic phasor.

```
∀ h ∈ {0}:
    a₀⁽ᴰ⁾(t) = ξ₀⁽ᴰ⁾(t)
∀ h ∉ {0}:
    aₕ⁽⁰⁾(t) = |2 ⋅ ξₕ⁽⁰⁾(t)| ∈ 𝐑⁺
    aₕ⁽¹⁾(t) = ℜ[2 ⋅ ξₕ⁽¹⁾(t) ⋅ exp(-im ⋅ ϕₕ⁽⁰⁾(t))] ∈ 𝐑
    aₕ⁽²⁾(t) = ℜ[2 ⋅ ξₕ⁽²⁾(t) ⋅ exp(-im ⋅ ϕₕ⁽⁰⁾(t))] + aₕ⁽⁰⁾(t) ⋅ ϕₕ⁽¹⁾(t)² ∈ 𝐑
```

See: [Assessing Synchrophasor Estimates of an Event Captured by a Phasor  Measurement Unit, pg. 3112](https://ieeexplore.ieee.org/document/9239915)

Input:

  * `sol::AbstractDTFTSolution`   | DTFT solution struct [-]
  * `D::Int`                      | degree of the derivative [-], default=0
  * `H::Int`                      | harmonic number [-], default=1

Output:

  * `a::Vector{<:Real}`           | amplitude aₕ⁽ᴰ⁾(t) [?]
