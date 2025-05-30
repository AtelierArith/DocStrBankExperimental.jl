```
coeftable(model::StatisticalModel; level::Real=0.95)
```

モデルの係数と関連統計を含むテーブルを返します。`level`は信頼区間のレベルを決定します（デフォルトは95%です）。

返される`CoefTable`オブジェクトは、[Tables.jl](https://github.com/JuliaData/Tables.jl/)インターフェースを実装しており、例えば`using DataFrames; DataFrame(coeftable(model))`を介して`DataFrame`に変換できます。
