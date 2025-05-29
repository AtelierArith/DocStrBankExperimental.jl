```
MapNode{T,C}
```

[`treemap`](@ref) によって返される木のノードです。これは、関数呼び出しの結果である値と、同じく `MapNode` 型の子供の配列で構成されています。

すべての `MapNode` は [`IndexedChildren`](@ref) 特性を持つ木であり、したがって [`getdescendant`](@ref) を介してインデックス付けをサポートしています。

ラップされた値を取得するには、[`AbstractTrees.nodevalue`](@ref) または `mapnode.value` を使用してください。
