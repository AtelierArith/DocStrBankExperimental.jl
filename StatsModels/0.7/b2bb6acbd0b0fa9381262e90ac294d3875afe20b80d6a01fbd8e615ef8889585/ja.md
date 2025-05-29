```
apply_schema(t::AbstractTerm, schema::StatsModels.FullRank, Mod::Type)
```

スキーマを適用します。これは、フルランクでないモデル行列が生成される場合、カテゴリカル項がフルランクに「昇格」されるべきであると仮定しています（$k$レベルのカテゴリカル変数は、標準のコントラストコーディングスキームでの$k-1$ではなく、$k$列を生成します）。このステップは、`Mod <: StatisticalModel`の場合に自動的に適用されますが、他のタイプのモデルは、次のようなメソッドを追加することでオプトインできます。

```
StatsModels.apply_schema(t::FormulaTerm, schema::StatsModels.Schema, Mod::Type{<:MyModelType}) =
    apply_schema(t, StatsModels.FullRank(schema), mod)
```

カテゴリカルデータのモデリングに関する詳細は、ドキュメントの[Modeling categorical data](@ref)のセクションを参照してください。
