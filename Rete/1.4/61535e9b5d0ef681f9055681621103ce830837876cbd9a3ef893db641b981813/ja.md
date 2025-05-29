```
ensure_memory_node(root::AbstractReteRootNode, typ::Type)::IsaTypeNode
```

指定されたタイプのメモリノードを見つけるか、作成してネットワークに追加します。

デフォルトはIsaMemoryNodeを作成することです。この関数を`Type`に特化させて、そのタイプに対してどのタイプのメモリノードを使用するかを制御します。
