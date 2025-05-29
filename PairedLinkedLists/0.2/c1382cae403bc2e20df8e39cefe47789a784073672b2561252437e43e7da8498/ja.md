```
node = PairedListNode(list::PairedLinkedList, data)
```

指定された `list` に属する `PairedListNode` を作成します。ノードは親リストへの参照 `list` と提供された `data` を含みますが、`list` への特定の挿入ポイントはありません（[`insertafter!`](@ref) を参照）。

`node.prev` と `node.next` は、それぞれリストの前のノードと次のノードを表します。

ノードの `target` は常に自分自身への参照（ペアでないノードを示す）か、親 `list` の `target` に属するノードである必要があります。

`target` リンクは `PairedListNode` に対して相互に関連付けられていると仮定されます。例えば、`node === node.target.target` は `true` であるべきです。一方向のリスト間リンクについては、[`TargetedListNode`](@ref) を参照してください。

また、[`PairedLinkedList`](@ref)、[`ListNode`](@ref)、[`TargetedListNode`](@ref) も参照してください。
