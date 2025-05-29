```julia
ApatiteHe(T=Float64;
    age::Number = T(NaN),
    age_sigma::Number = T(NaN),
    offset::Number = zero(T),
    r::Number, 
    dr::Number = one(T), 
    U238::Number, 
    Th232::Number, 
    Sm147::Number = zero(T), 
    U238_matrix::Number = zero(T), 
    Th232_matrix::Number = zero(T), 
    Sm147_matrix::Number = zero(T), 
    volumeweighting::Symbol = :spherical,
    agesteps::AbstractRange,
)
```

`age` ± `age_sigma` [Ma] の生のヘリウム年代を持つアパタイトを表す `ApatiteHe` クロノメーターを構築します。半径 `r` [μm] と、`U238`、`Th232`、`Sm147` [PPMW] で指定された均一な U、Th、Sm 濃度を持ちます。現在の U-235/U-238 比は 1/137.818 と仮定されます。

空間の離散化は `dr` [μm] の半径ステップに従い、時間の離散化は Ma で指定された `agesteps` 範囲による年代ステップに従います。
