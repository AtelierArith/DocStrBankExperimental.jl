```
WignerHindex(ℓ, m′, m, m′ₘₐₓ)
```

配列を「ウェッジ」するためのインデックス。

関連項目としては [`WignerHsize`](@ref) と [`WignerHrange`](@ref) を参照してください。

# 注意事項

ここでは、m≥|m'| のデータのみが保存され、対応する値のみが渡されると仮定しています。また、|m|≤ℓ および |m'|≤ℓ であると仮定しています。これらのいずれもチェックされません。この関数がインデックスを付けるウェッジ配列は次のように順序付けられています。

```
[
    H(ℓ, m′, m) for ℓ ∈ 0:ℓₘₐₓ
    for m′ ∈ -min(ℓ, m′ₘₐₓ):min(ℓ, m′ₘₐₓ)
    for m ∈ abs(m′):ℓ
]
```
