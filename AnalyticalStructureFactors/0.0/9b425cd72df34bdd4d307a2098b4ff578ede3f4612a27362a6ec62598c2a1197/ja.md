```
S_HS_Baxter_mixture(σ_vector::AbstractVector{T}, ρ_vector::AbstractVector{T}, k_wavevector::T) where {T<:AbstractFloat}
```

バクスターのQ行列形式（パーカス-イェビック近似）を使用して、多成分ハードスフェア混合物の部分構造因子行列S(k)を計算します。 S(k) = inv(Qᴴ(k) * Q(k))
