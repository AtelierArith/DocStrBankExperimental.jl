```julia
SphericalAr(T=Float64;
    age::Number = T(NaN),
    age_sigma::Number = T(NaN),
    offset::Number = zero(T),
    r::Number, 
    dr::Number = one(T), 
    K40::Number=16.34, 
    agesteps::AbstractRange,
)
```

`SphericalAr` クロノメーターを構築し、原始的なアルゴン年齢 `age` ± `age_sigma` [Ma] を持つ鉱物、均一な拡散率、半径 `r` [μm]、および `K40` [PPM] で指定された均一な K-40 濃度を表します。

空間の離散化は半径ステップ `dr` [μm] に従い、時間の離散化は `agesteps` 範囲で指定された年齢ステップに従います、単位は Ma です。
