```
component_costs(mg_project::Project, lifetime::Real,
    investment::Real, replacement::Real, salvage::Real,
    om_annual::Real, fuel_annual::Real,
    salvage_type::SalvageType=LinearSalvage)
```

マイクログリッドの寿命にわたるコンポーネントの正味現在コスト要因を計算します。

コスト評価は名目および年間コスト要因から行われます。

### 引数

  * mg_project: マイクログリッドプロジェクトの説明（例：割引率と寿命を含む）
  * lifetime: コンポーネントの有効寿命
  * investment: 初期投資コスト
  * replacement: 各交換の名目コスト
  * salvage: コンポーネントがゼロの劣化で売却された場合の名目残存価値
  * om_annual: 年間の名目運用および保守（O&M）コスト
  * fuel_annual: 年間の名目燃料コスト
  * salvage_type: 残存価値計算のための式の選択、可能な `SalvageType` 列挙型の値の中から（デフォルトは `LinearSalvage`、または `ConsistentSalvage`、`SalvageType` ドキュメントを参照）
