```
filter_nodes(datadigraph, filter_value, attribute = dg.node_data.attributes[1]; fn = isless)
```

グラフのノードを削除します。ノードの `attribute` に関するデータが `filter_value` に対して `fn` の基準を満たさない場合です。`attribute` が指定されていない場合、これは DataDiGraph の `NodeData` 内の最初の属性にデフォルト設定されます。

`fn` は、ノードの属性に関するデータの入力と `filter_value` を受け取り、真または偽を返す関数です。
