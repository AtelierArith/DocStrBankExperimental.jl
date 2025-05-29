```
filter_edges(datagraph, filter_value, attribute = dg.edge_data.attributes[1]; fn = isless)
```

グラフのエッジを削除します。`attribute`のデータが`filter_value`に対して`fn`の基準を満たさない場合です。`attribute`が指定されていない場合、これはDataGraphの`EdgeData`内の最初の属性にデフォルト設定されます。

`fn`は、属性に関するエッジのデータの入力と`filter_value`を受け取り、真または偽を返す関数です。
