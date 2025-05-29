```julia
struct DiffObjective{O<:ModelWrappers.Objective, T<:BaytesDiff.AbstractDifferentiableTune}
```

ADバックエンドと構成に関する追加情報を持つ目的の構造体。

# フィールド

  * `objective::ModelWrappers.Objective`: 制約のない空間におけるパラメータベクトルの関数としての目的。
  * `tune::BaytesDiff.AbstractDifferentiableTune`: 自動微分の構成。
