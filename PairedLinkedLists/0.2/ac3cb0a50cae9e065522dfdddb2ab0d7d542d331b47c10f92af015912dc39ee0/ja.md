```
node = ListNode(list::DoublyLinkedList [, data])
```

指定された `list` に属する `ListNode` を作成します。ノードは親リストへの参照 `list` を含み、提供された `data` を含みますが、`list` への特定の挿入ポイントはありません（[`insertafter!`](@ref）を参照）。

`node.prev` と `node.next` は、それぞれリストの前のノードと次のノードを表します。

さらに [`DoublyLinkedList`](@ref)、[`PairedListNode`](@ref)、[`TargetedListNode`](@ref) を参照してください。
