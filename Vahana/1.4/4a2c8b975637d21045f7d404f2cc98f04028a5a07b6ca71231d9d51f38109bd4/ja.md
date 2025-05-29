```
vahanasimplegraph(sim::Simulation; [agenttypes::Vector{DataType}, edgetypes::Vector{DataType}, show_ignorefrom_warning = true])
```

指定された `agenttypes` タイプのエージェントを持つノードと、指定された `edgetypes` タイプのエッジを持つサブグラフを作成します。エッジの両隣接ノードタイプが `agenttypes` に含まれている必要があります。

`agenttypes` と `edgetypes` のデフォルト値は、すべて登録されたエージェント/エッジタイプです（[`register_agenttype!`](@ref) および [`register_edgetype!`](@ref) を参照）。

このサブグラフは、Graphs.jl パッケージの AbstractSimpleGraph インターフェースを実装しています。

エッジタイプには :IgnoreFrom プロパティを持たない必要があります。`edgetypes` ベクターにこのプロパティを持つエッジタイプがある場合、警告が表示され、これらのエッジは無視されます。警告は `show_ignorefrom_warning` を false に設定することで抑制できます。

!!! warning
    AbstractGraph インターフェースは、2つのノード間に複数のエッジを許可しますが、グラフをバイナリ（スパース）行列に変換する関数など、一部の関数はこれらのグラフに対して未定義の結果を生成する可能性があります。したがって、この関数は注意して使用してください。

