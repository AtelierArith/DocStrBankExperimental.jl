```
IS_HS_Baxter_mixture(σ_vector::AbstractVector{T}, ρ_vector::AbstractVector{T}, k_wavevector::T) where {T<:AbstractFloat}
```

Calculates the inverse of the partial structure factor matrix, S⁻¹(k), for a multi-component hard-sphere mixture using Baxter's Q-matrix formalism. S⁻¹(k) = Qᴴ(k) * Q(k)
