```
node = PairedSkipNode(list::SkipList [, data])
```

Create a `PairedSkipNode` belonging to the specified `list`. The node contains a reference `list` to the parent [skip list](https://en.wikipedia.org/wiki/Skip_list) and contains the provided `data`, but it has no specific insertion point into `list` (see [`insertafter!`](@ref)).

`node.prev` and `node.next` represent the previous and next nodes, respectively, of a list. `node.up` and `node.bottom` represent the nodes in adjacent levels within the skip list data structure.

A node's `target` should always either be a reference to itself (denoting unpaired node) or a node belonging to the `target` of its parent `list`.

The `target` link is assumed to be reciprocated for a `PairedSkipNode`. For example, `node === node.target.target` should be `true`.

See also [`PairedSkipList`](@ref), [`SkipNode`](@ref)
