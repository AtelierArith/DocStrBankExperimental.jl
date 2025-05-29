```
ABMObservable(model; adata, mdata, when) → abmobs
```

`abmobs` には、エージェントベースモデルをインタラクティブにステップするために必要なすべての情報が含まれており、インタラクティブにステップしながらデータを収集することもできます。 `ABMObservable` は [`abmplot`](@ref) によっても返されます。

`Agents.step!(abmobs, t)` を呼び出すと、モデルは `t` 時間だけステップし、[`Agents.run!`](@ref) のようにデータを収集します。

フィールド `abmobs.model, abmobs.adf, abmobs.mdf` は *observable* であり、[`AgentBasedModel`](@ref) と収集されたデータを持つエージェントおよびモデルのデータフレームを含んでいます。データは、`adata, mdata, when` キーワードを使用して、[`Agents.run!`](@ref) で説明されているように収集されます。すべての3つのobservableは、ステッピング時に（意味がある場合に）更新されます。

すべてのプロットとインタラクティビティは、これらのobservableを `lift` することによって定義されるべきです。
