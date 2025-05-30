```
set_model_geometry(reaction, model)
```

オプション: [`Domain`](@ref) `grid`, `data_dims` を定義します。

ドメインごとに1つの反応がグリッド（[`AbstractMesh`](@ref) サブタイプ）を作成し、`domain.grid` フィールドを設定することができます。

ドメインごとに複数の反応が [`set_data_dimension!`](@ref) を呼び出して（異なる）名前付きデータ次元（例: 波長グリッド）を定義することができます。
