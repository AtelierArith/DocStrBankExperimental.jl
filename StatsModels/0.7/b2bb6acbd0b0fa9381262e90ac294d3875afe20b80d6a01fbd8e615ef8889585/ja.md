```
apply_schema(t::AbstractTerm, schema::StatsModels.FullRank, Mod::Type)
```

スキーマを適用します。これは、フルランクでないモデル行列が生成される場合、カテゴリカル項がフルランクに「昇格」されるべきであると仮定しています（$k$ レベルのカテゴリカル変数は、標準のコントラストコーディングスキームで $k-1$ ではなく $k$ 列を生成します）。このステップは `Mod <: StatisticalModel` の場合に自動的に適用されますが、他のタイプのモデルは次のようにメソッドを追加することでオプトインできます。

```
StatsModels.apply_schema(t::FormulaTerm, schema::StatsModels.Schema, Mod::Type{<:MyModelType}) =
    apply_schema(t, StatsModels.FullRank(schema), mod)
```

カテゴリカルデータのモデル化に関する詳細は、ドキュメントの [Modeling categorical data](@ref) セクションを参照してください。
