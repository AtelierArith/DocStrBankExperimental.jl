```
vahanagraph(sim::Simulation; [agenttypes::Vector{DataType}, edgetypes::Vector{DataType}, show_ignorefrom_warning = true, drop_multiedges = false])
```

`agenttypes` のタイプのエージェントを持つすべてのノードと、`edgetypes` のタイプを持ち、両隣のエージェントが `agenttypes` のタイプであるすべてのエッジを持つサブグラフを作成します。

`agenttypes` と `edgetypes` のデフォルト値は、すべて登録されたエージェント/エッジタイプです（[`register_agenttype!`](@ref) および [`register_edgetype!`](@ref) を参照）。

このサブグラフは Graphs.jl パッケージの AbstractGraph インターフェースを実装しているため、例えば GraphMakie を使用してサブグラフを視覚化できます。[`create_graphplot`](@ref) も参照してください。

AbstractGraph インターフェースは、2つのノード間の複数のエッジを許可しますが、いくつかの関数（例えば、グラフをバイナリ（スパース）行列に変換する関数）は、これらのグラフに対して未定義の結果を生成する可能性があります。例えば、GraphMakie.jl から graphplot が呼び出された場合です。キーワード `drop_multiedges` が true であり、複数のエッジがある場合、生成されたグラフには、edgetypes ベクターの最初のタイプのエッジのみが追加されます。

エッジタイプは :IgnoreFrom プロパティを持ってはいけません。`edgetypes` ベクターにこのプロパティを持つエッジタイプがある場合、警告が表示され、これらのエッジは無視されます。警告は `show_ignorefrom_warning` を false に設定することで抑制できます。
