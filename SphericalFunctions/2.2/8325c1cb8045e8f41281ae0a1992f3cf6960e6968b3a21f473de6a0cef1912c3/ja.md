```
WignerDsize(ℓₘₐₓ, m′ₘₐₓ=ℓₘₐₓ)
```

ウィグナー 𝔇 行列の総サイズを計算します

関連情報として [`WignerDrange`](@ref) と [`WignerDindex`](@ref) を参照してください。

# 注意事項

これはウィグナー 𝔇 行列が次のように配置されていると仮定します

```
[
    𝔇(ℓ, m′, m)
    for ℓ ∈ ℓₘᵢₙ:ℓₘₐₓ
    for m′ ∈ -min(ℓ, m′ₘₐₓ):min(ℓ, m′ₘₐₓ)
    for m ∈ -ℓ:ℓ
]
```
