```
const FESpaceHierarchy = HierarchicalArray{<:FESpaceHierarchyLevel}
```

`FESpaceHierarchy`は`FESpaceHierarchyLevel`オブジェクトの階層配列です。適応された/再配分された有限要素空間と対応するサブコミュニケーターを格納します。

便利のために、`FESpace`のAPIの一部を実装しています。
