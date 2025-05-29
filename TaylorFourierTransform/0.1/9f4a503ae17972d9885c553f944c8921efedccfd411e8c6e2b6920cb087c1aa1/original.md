```
TaylorFourierTransform.ar_phasor(sol::TaylorFourierTransform.AbstractDTFTSolution, D::Int=0, H::Int=1)
```

Function to obtain the D-th-degree derivative of the Hth-harmonic anti-rotating  dynamic phasor.

```
∀ h ∈ {0}:
    ψ₀⁽ᴰ⁾(t) = ξ₀⁽ᴰ⁾(t) ∈ ℝ
∀ h ∉ {0}:
    ψₕ⁽ᴰ⁾(t) = ξₕ⁽ᴰ⁾(t) exp(-im ωₕ t) ∈ 𝐂
```

Input:

  * `sol::AbstractDTFTSolution`   | DTFT solution struct [-]
  * `D::Int`                      | degree of the derivative [-], default=0
  * `H::Int`                      | harmonic number [-], default=1

Output:

  * `ψ::Vector{<:Complex}`        | anti-rotating dynamic phasor ψₕ⁽ᴰ⁾(t) [?]
