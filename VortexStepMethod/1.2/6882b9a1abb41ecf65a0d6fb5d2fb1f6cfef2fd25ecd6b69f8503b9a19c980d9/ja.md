```
翼
```

複数のセクションで構成される翼を表し、空力特性を持っています。

# フィールド

  * `n_panels::Int16`: 空力メッシュ内のパネル数
  * `n_groups::Int16`: パネルグループの数
  * `spanwise_distribution`::PanelDistribution: [PanelDistribution](@ref)
  * `spanwise_direction::MVec3`: 翼のスパン方向ベクトル
  * `sections::Vector{Section}`: 翼のセクションのベクトル、参照: [Section](@ref)
  * `refined_sections::Vector{Section}`: 洗練された翼のセクションのベクトル、参照: [Section](@ref)
  * `remove_nan::Bool`: 補間からNaNを削除するかどうか
