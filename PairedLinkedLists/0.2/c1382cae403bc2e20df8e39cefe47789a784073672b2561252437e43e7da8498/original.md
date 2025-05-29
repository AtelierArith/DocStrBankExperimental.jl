```
node = PairedListNode(list::PairedLinkedList, data)
```

Create a `PairedListNode` belonging to the specified `list`. The node contains a reference `list` to the parent list and  contains the provided `data`, but it has no specific insertion point into `list` (see [`insertafter!`](@ref)).

`node.prev` and `node.next` represent the previous and next nodes, respectively, of a list.

A node's `target` should always either be a reference to itself (denoting unpaired node) or a node belonging to the `target` of its parent `list`.

The `target` link is assumed to be reciprocated for a `PairedListNode`. For example, `node === node.target.target` should be `true`. For one-way inter-list links, see [`TargetedListNode`](@ref).

See also [`PairedLinkedList`](@ref), [`ListNode`](@ref), [`TargetedListNode`](@ref).
