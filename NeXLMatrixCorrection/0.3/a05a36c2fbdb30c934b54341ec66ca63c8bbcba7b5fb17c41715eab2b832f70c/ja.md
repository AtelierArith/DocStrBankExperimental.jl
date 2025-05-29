```
kcoating(ty::Type{<:MatrixCorrection}, subtrate::Material, coating::Material, cxr::CharXRay, e0::AbstractFloat, toa::AbstractFloat, τ::AbstractFloat)
```

指定された基板上に質量厚さ τ (g/cm²) のコーティングの k 比を推定します。コーティングの標準はコーティングと同じ材料であると仮定されます。
