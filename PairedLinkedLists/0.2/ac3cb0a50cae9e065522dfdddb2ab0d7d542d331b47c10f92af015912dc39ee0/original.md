```
node = ListNode(list::DoublyLinkedList [, data])
```

Create a `ListNode` belonging to the specified `list`. The node contains a reference `list` to the parent list and  contains the provided `data`, but it has no specific insertion point into `list` (see [`insertafter!`](@ref)).

`node.prev` and `node.next` represent the previous and next nodes, respectively, of a list.

See also [`DoublyLinkedList`](@ref), [`PairedListNode`](@ref), [`TargetedListNode`](@ref).
