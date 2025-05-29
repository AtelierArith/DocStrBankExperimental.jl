```
S_HS_Baxter_mixture(σ_vector::AbstractVector{T}, ρ_vector::AbstractVector{T}, k_wavevector::T) where {T<:AbstractFloat}
```

Calculates the partial structure factor matrix S(k) for a multi-component hard-sphere mixture using Baxter's Q-matrix formalism (Percus-Yevick approximation). S(k) = inv(Qᴴ(k) * Q(k))
