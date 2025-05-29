```
aggregate(datadigraph, node_list, aggregated_node_name;
            node_fn = mean, edge_fn = mean, save_agg_edge_data = false,
            agg_edge_fn = mean, agg_edge_val = 0, node_attributes_to_add = String[]
)
```

`node_list`内のすべてのノードを1つのノードに集約し、そのノードを`aggregated_node_name`と呼びます。ノードに重みや属性値が定義されている場合、これらの値は`node_fn`関数を介して結合されます。`node_fn`のデフォルトはStatistics.meanで、`node_list`内のノードのデータを平均化します。エッジデータも、`node_list`内の2つ以上のノードが同じノードに接続されている場合、`edge_fn`を介して結合されます。`edge_fn`のデフォルトも`Statistics.mean`です。

`node_list`内のノード間にエッジが存在する場合、これらのエッジのデータは`save_agg_edge_data = true`を設定することで、`aggregated_node_name`ノードにオプションで保存できます。trueの場合、これらのエッジのデータは`agg_edge_fn`を使用して集約されます。ユーザーがこのデータの新しい属性名を定義したい場合は、`node_attributes_to_add`にベクトルを渡すことができます。ベクトルが定義されていない場合、データは`edge_data`属性の名前の下で集約されます。集約されたノードを除くすべてのノードは、これらの属性が`agg_edge_val`として初期化されます。
