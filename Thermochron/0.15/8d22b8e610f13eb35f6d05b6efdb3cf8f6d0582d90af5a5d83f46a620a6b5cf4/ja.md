```julia
PlanarHe(T=Float64;
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

`age` ± `age_sigma` [Ma] の生のヘリウム年齢を持つ鉱物を表す `PlanarHe` クロノメーターを構築します。均一な拡散性、半幅 `r` [μm]、および `U238`、`Th232`、`Sm147` [PPM] で指定された均一な U、Th、Sm 濃度を持ちます。（現在の U-235/U-238 比率は 1/137.818 と仮定されています）

空間の離散化は `dr` [μm] の半幅ステップに従い、時間の離散化は Ma で指定された `agesteps` 範囲による年齢ステップに従います。
