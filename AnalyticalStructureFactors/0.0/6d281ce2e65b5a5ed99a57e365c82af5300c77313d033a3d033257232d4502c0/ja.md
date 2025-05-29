```
IS_HS_Baxter_mixture(σ_vector::AbstractVector{T}, ρ_vector::AbstractVector{T}, k_wavevector::T) where {T<:AbstractFloat}
```

バクスターのQ行列形式を使用して、多成分ハードスフェア混合物の部分構造因子行列の逆行列S⁻¹(k)を計算します。 S⁻¹(k) = Qᴴ(k) * Q(k)
