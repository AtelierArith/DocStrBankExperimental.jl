```
TaylorFourierTransform.signal(sol::TaylorFourierTransform.AbstractDTFTSolution)
```

Function to obtain the overall signal.

```
s(t) = ∑ₕ ξₕ⁽⁰⁾(t) + conj(ξₕ⁽⁰⁾(t)) ∈ 𝐑
```

Input:

  * `sol::AbstractDTFTSolution`   | DTFT solution struct [-]

Output:

  * `s::Vector{<:Real}`           | signal s(t) [?]
