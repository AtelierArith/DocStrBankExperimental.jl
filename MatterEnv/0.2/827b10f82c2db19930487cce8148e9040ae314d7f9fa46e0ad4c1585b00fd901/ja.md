```
save_procar(projection::Projection,
    kpoints::Array{KPoint, 1},
    bands::AbstractBands,
    filename::String="PROCAR";
    squared_only::Bool=true)
```

波動関数⟨Yₗₘ|ϕₙₖ⟩のプロジェクションをPROCARファイルに保存します。

# 引数

  * `projection::AbstractProjection`: 波動関数のプロジェクション
  * `kpoints::Array{KPoint, 1}`: k点のメタデータ
  * `bands::AbstractBands`: バンドのメタデータ
  * `filename::String="PROCAR"`: 出力ファイルの名前
  * `squared_only::Bool=true`: 二乗プロジェクション|⟨Yₗₘ|ϕₙₖ⟩|²のみ出力するかどうか
