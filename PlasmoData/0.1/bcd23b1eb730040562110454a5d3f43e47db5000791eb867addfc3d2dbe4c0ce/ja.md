```
filter_nodes(datagraph, filter_value, attribute = dg.node_data.attributes[1]; fn = isless)
```

グラフのノードを削除します。ノードの `attribute` に関するデータが `filter_value` に対して `fn` の基準を満たさない場合です。`attribute` が指定されていない場合、これは DataGraph の `NodeData` 内の最初の属性にデフォルト設定されます。

`fn` は、ノードの属性に関するデータと `filter_value` を入力として受け取り、真または偽を返す関数です。
