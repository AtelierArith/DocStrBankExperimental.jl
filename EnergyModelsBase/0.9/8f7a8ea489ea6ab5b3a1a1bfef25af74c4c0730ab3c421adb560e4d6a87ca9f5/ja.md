```
create_node(m, n::Availability, 𝒯, 𝒫, modeltype::EnergyModel)
```

`Availability`のすべての制約を設定します。指定されていないすべての`Availability`のサブタイプのフォールバックオプションとして機能します。

`Availability`ノードはルーティングノードとして見ることができます。異なる`Availability`ノード間の輸送を関連コストとともに含めたい場合を除いて、利用可能なノードが1つ以上必要であるとは限りません（現時点では実装されていません）。
