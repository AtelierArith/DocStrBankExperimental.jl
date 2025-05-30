```
WignerDrange(ℓₘₐₓ, m′ₘₐₓ=ℓₘₐₓ)
```

(ℓ, m', m) インデックスの配列を 𝔇 配列のように作成します

参照してください [`WignerDsize`](@ref) と [`WignerDindex`](@ref)。

# 注意事項

これは Wigner 𝔇 行列が次のように配置されていると仮定します

```
[
    𝔇(ℓ, m′, m)
    for ℓ ∈ ℓₘᵢₙ:ℓₘₐₓ
    for m′ ∈ -min(ℓ, m′ₘₐₓ):min(ℓ, m′ₘₐₓ)
    for m ∈ -ℓ:ℓ
]
```
