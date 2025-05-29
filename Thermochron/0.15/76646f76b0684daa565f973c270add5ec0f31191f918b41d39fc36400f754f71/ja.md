```julia
PlanarAr(T=Float64;
    age::Number = T(NaN),
    age_sigma::Number = T(NaN),
    offset::Number = zero(T),
    r::Number, 
    dr::Number = one(T), 
    K40::Number=16.34, 
    agesteps::AbstractRange,
)
```

`age` ± `age_sigma` [Ma] の生のアルゴン年齢を持つ鉱物を表す `PlanarAr` クロノメーターを構築します。均一な拡散率、半径 `r` [μm]、および `K40` [PPM] で指定された均一な K-40 濃度を持ちます。

空間の離散化は `dr` [μm] の半幅ステップに従い、時間の離散化は Ma で指定された `agesteps` 範囲による年齢ステップに従います。
