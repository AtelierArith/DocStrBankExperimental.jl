```
TemporalBrains(; dir = nothing, threshold_value = 0.6)
```

TemporalBrainsデータセットには、[Human Connectome Project (HCP)](https://www.humanconnectome.org/study/hcp-young-adult/document/extensively-processed-fmri-data-documentation)から得られた1000人の被験者の安静時fMRIデータに基づく時間的脳ネットワーク（`TemporalSnapshotsGraph`として）コレクションが含まれています。

27のスナップショットそれぞれのノード数は102に固定されており、エッジは時間とともに変化します。

各`Graph`スナップショットにおいて、ノードの特徴はそのスナップショット中のノードの平均活性を表し、`Graphs.node_data`に含まれています。

各`TemporalSnapshotsGraph`には、性別（男性は"M"、女性は"F"）と年齢範囲（22-25、26-30、31-35、36+）を表すラベルがあり、これは`graph_data`の名前付きタプルとして含まれています。

`threshold_value`はエッジの重みを二値化するために使用され、デフォルトでは0.6に設定されています。
