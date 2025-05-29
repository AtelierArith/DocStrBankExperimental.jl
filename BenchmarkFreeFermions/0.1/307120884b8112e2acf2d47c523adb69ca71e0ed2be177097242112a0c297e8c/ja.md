```
 GreenFunction(ξ::Vector{Float64}, V::Matrix{F}, β::Real; τ::Number=0.0) -> G::Matrix{F}
 GreenFunction(ξ::Vector{Float64}, V::Matrix{F}, β::Real,
 i::Int64, j::Int64;
 τ::Number=0.0,
 reverse::Bool = false) -> Gij::F
```

グリーン関数 `Gij(τ) = ⟨c_i(τ) c_j^dag⟩` を計算します（係数を除く）シフトされた単一粒子スペクトル `ξ = ϵ - μ` と、`Tij = - V diagm(ϵ) V'` から得られた固有ベクトル `V` を用いて。

# Kwargs

```
 reverse::Bool = false
```

`reverse = true` の場合は、代わりに `⟨c_i^dag(τ) c_j⟩` を返します。
