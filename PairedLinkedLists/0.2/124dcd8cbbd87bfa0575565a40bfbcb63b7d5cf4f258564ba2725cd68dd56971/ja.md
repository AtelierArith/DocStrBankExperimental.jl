```
node = PairedSkipNode(list::SkipList [, data])
```

指定された `list` に属する `PairedSkipNode` を作成します。このノードは親 [スキップリスト](https://en.wikipedia.org/wiki/Skip_list) への参照 `list` を含み、提供された `data` を含みますが、`list` への特定の挿入ポイントはありません（[`insertafter!`](@ref）を参照）。

`node.prev` と `node.next` は、それぞれリストの前のノードと次のノードを表します。`node.up` と `node.bottom` は、スキップリストデータ構造内の隣接レベルのノードを表します。

ノードの `target` は常に自分自身への参照（ペアでないノードを示す）か、親 `list` の `target` に属するノードである必要があります。

`target` リンクは `PairedSkipNode` に対して相互に関連付けられていると仮定されます。例えば、`node === node.target.target` は `true` であるべきです。

さらに [`PairedSkipList`](@ref)、[`SkipNode`](@ref) を参照してください。
