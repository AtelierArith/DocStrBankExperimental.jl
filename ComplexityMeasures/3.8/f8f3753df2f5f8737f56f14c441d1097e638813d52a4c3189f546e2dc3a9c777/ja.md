```
missing_outcomes(o::OutcomeSpace, x; all = false) → n::Int
```

データに指定された `o` に基づいて、入力データ `x` に存在しない欠損結果の数 `n` をカウントします。この関数はカウントベースの結果空間にのみ機能し、それ以外の場合は [`missing_probabilities`](@ref) を使用してください。

関連情報: [`MissingDispersionPatterns`](@ref).
