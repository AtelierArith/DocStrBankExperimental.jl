```
TaylorFourierTransform.phasor(sol::TaylorFourierTransform.AbstractDTFTSolution, D::Int=0, H::Int=1)
```

Function to obtain the D-th-degree derivative of the Hth-harmonic dynamic  phasor. For the zeroth-harmonic dynamic phasor, only the real part of the  dynamic phasor is returned.

```
∀ h ∈ {0}:
    ξ₀⁽ᴰ⁾(t) ∈ ℝ
∀ h ∉ {0}:
    ξₕ⁽ᴰ⁾(t) ∈ ℂ
```

Input:

  * `sol::AbstractDTFTSolution`   | DTFT solution struct [-]
  * `D::Int`                      | degree of the derivative [-], default=0
  * `H::Int`                      | harmonic number [-], default=1

Output:

  * `ξ::Vector{<:Complex}`        | dynamic phasor ξₕ⁽ᴰ⁾(t) [?]
