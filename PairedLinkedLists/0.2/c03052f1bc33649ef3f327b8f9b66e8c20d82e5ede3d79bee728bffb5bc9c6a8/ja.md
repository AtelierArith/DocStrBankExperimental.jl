```
node = TargetListNode(list::AbstractTargetLinkedList, data, [target::AbstractListNode])
```

指定された `list` に属する `TargetedListNode` を作成します。ノードは親リストへの参照 `list` を含み、提供された `data` を含みますが、`list` への特定の挿入ポイントはありません（[`insertafter!`](@ref）を参照）。

`node.prev` と `node.next` は、それぞれリストの前のノードと次のノードを表します。

ノードの `target` は常に自分自身への参照（ペアがないノードを示す）であるか、親 `list` の `target` に属するノードである必要があります。

`PairedListNode` に対して `target` リンクは相互にされているとは限らないため、ターゲットノードには `target` フィールドがない場合もあります。双方向のリスト間リンクを保証するには、[`PairedListNode`](@ref) を参照してください。

また、[`TargetedLinkedList`](@ref)、[`PairedListNode`](@ref)、[`ListNode`](@ref) も参照してください。
