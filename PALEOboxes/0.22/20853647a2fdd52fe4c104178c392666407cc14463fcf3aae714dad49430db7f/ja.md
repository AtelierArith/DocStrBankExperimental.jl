```
set_model_geometry(reaction, model)
```

オプション: [`Domain`](@ref) `grid`、`data_dims`を定義します。

1つのドメインあたり1つの反応がグリッド（[`AbstractMesh`](@ref) サブタイプ）を作成し、`domain.grid` フィールドを設定することができます。

ドメインあたり複数の反応は、異なる名前のデータ次元（例: 波長グリッド）を定義するために [`set_data_dimension!`](@ref) を呼び出すことができます。
