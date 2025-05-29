```
function ref_add_core!(ref::Dict{Symbol,Any})
```

データ辞書から取得した一般的に使用される事前計算データを格納する辞書を返します。主にデータ型の変換、送信側システムでの負荷のフィルタリング、配電側システムでのスラック発電機の削除、グローバルに計算する必要があるシステム全体の値の格納に使用されます。一般的なキーには以下が含まれます：

  * `See ref_add_core!(ref) from PowerModels`),
  * `See ref_add_core!(ref) from PowerModelsDistribution`),
  * `:boundary` – ネットワーク内でアクティブな境界要素の集合、
  * `:arcs_boundary_from` – 集合 `[(i,b["f_bus"],b["t_bus"]) for (i,b) in ref[:boundary]]`、
  * `:arcs_boundary_to` – 集合 `[(i,b["t_bus"],b["f_bus"]) for (i,b) in ref[:boundary]]`、
  * `:arcs_boundary` – `arcs_boundary_from` と `arcs_boundary_to` の両方からの弧の集合、
  * `:bus_arcs_boundary_from` – マッピング `Dict(i => [(l,i,j) for (l,i,j) in ref[:arcs_boundary_from]])`、
  * `:bus_arcs_boundary_to` – マッピング `Dict(i => [(l,i,j) for (l,i,j) in ref[:arcs_boundary_to]])`。
