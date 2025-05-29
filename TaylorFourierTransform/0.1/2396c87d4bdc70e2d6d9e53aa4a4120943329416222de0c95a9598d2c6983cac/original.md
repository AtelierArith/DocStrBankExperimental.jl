```
TaylorFourierTransform.signal(sol::TaylorFourierTransform.AbstractDTFTSolution, H::Int)
```

Function to obtain the Hth-harmonic signal. 

```
∀ h ∈ {0}:
    s₀(t) = ξ₀⁽⁰⁾(t) ∈ 𝐑
∀ h ∉ {0}: 
    sₕ(t) = ℜ[ξₕ⁽⁰⁾(t) + conj(ξₕ⁽⁰⁾(t))] ∈ 𝐑
```

Note: In its essence, the real operator `ℜ[]``is unnecessary, however, it is  used to convert the complex number`x + j0`to a real number`x`. 

Input:

  * `sol::AbstractDTFTSolution`   | DTFT solution struct [-]
  * `H::Int`                      | harmonic number [-]

Output:

  * `s::Vector{<:Real}`           | signal sₕ(t) [?]
