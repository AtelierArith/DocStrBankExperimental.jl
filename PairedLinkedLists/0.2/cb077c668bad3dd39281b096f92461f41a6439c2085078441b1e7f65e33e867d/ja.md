```
node = SkipNode(list::SkipList [, data])
```

指定された `list` に属する `SkipNode` を作成します。このノードは親 [スキップリスト](https://en.wikipedia.org/wiki/Skip_list) への参照 `list` を含み、提供された `data` を含みますが、`list` への特定の挿入ポイントはありません（[`insertafter!`](@ref) を参照）。

`node.prev` と `node.next` は、それぞれリストの前のノードと次のノードを表します。`node.up` と `node.bottom` は、スキップリストデータ構造内の隣接レベルのノードを表します。

他にも [`SkipList`](@ref)、[`PairedSkipNode`](@ref) を参照してください。
