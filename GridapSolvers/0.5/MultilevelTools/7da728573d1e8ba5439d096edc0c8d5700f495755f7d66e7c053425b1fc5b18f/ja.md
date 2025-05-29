```
const ModelHierarchy = HierarchicalArray{<:ModelHierarchyLevel}
```

`ModelHierarchy` は `ModelHierarchyLevel` オブジェクトの階層配列です。適応された/再配分されたモデルと対応するサブコミュニケーターを格納します。

便利のために、`DiscreteModel` のいくつかのAPIを実装しています。
