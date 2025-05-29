```julia
SphericalHe(T=Float64;
    age::Number = T(NaN),
    age_sigma::Number = T(NaN),
    offset::Number = zero(T),
    stoppingpower::Number = T(1.189),
    r::Number, 
    dr::Number = one(T), 
    U238::Number, 
    Th232::Number, 
    Sm147::Number = zero(T), 
    U238_matrix::Number = zero(T), 
    Th232_matrix::Number = zero(T), 
    Sm147_matrix::Number = zero(T), 
    agesteps::AbstractRange,
)
```

`SphericalHe` クロノメーターを構築し、原始ヘリウム年齢 `age` ± `age_sigma` [Ma] を持つ鉱物を表し、均一な拡散率、半径 `r` [μm]、および `U238`、`Th232`、`Sm147` [PPM] で指定された均一な U、Th、Sm 濃度を持ちます。（現在の U-235/U-238 比は 1/137.818 と仮定されています）

空間の離散化は半径ステップ `dr` [μm] に従い、時間の離散化は `agesteps` 範囲で指定された年齢ステップに従います。
