```
SellmeierModel{N,T}
```

Sellmeier model representing the Sellmeier equation ε(λ) = 1 + ∑ᵢ [Bᵢ λ² / (λ² - Cᵢ)], where the sum is for `1 ≤ i ≤ N`.

# Fields

  * `str::SVector{N,T<:Real}`: `str[i]` is the strength of the `i`th term in the Sellmeier equation; corresponds to Bᵢ.
  * `λres::SVector{N,T<:Real}`: `λres[i]` is the resonance wavelength of the `i`th term in the Sellmeier equation; corresponds to √Cᵢ.
