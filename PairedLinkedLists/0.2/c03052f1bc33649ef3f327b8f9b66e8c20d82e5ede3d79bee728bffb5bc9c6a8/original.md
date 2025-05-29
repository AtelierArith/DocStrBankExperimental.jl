```
node = TargetListNode(list::AbstractTargetLinkedList, data, [target::AbstractListNode])
```

Create a `TargetedListNode` belonging to the specified `list`. The node contains a reference `list` to the parent list and  contains the provided `data`, but it has no specific insertion point into `list` (see [`insertafter!`](@ref)).

`node.prev` and `node.next` represent the previous and next nodes, respectively, of a list.

A node's `target` should always either be a reference to itself (denoting unpaired node) or a node belonging to the `target` of its parent `list`.

The `target` link is *not* assumed to be reciprocated for a `PairedListNode`, as the targeted node may not even have a `target` field.  For guranteed two-way inter-list links, see [`PairedListNode`](@ref).

See also [`TargetedLinkedList`](@ref), [`PairedListNode`](@ref), [`ListNode`](@ref).
