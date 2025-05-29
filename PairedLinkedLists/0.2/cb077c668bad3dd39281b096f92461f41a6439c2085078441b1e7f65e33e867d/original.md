```
node = SkipNode(list::SkipList [, data])
```

Create a `SkipNode` belonging to the specified `list`. The node contains a reference `list` to the parent [skip list](https://en.wikipedia.org/wiki/Skip_list) and contains the provided `data`, but it has no specific insertion point into `list` (see [`insertafter!`](@ref)).

`node.prev` and `node.next` represent the previous and next nodes, respectively, of a list. `node.up` and `node.bottom` represent the nodes in adjacent levels within the skip list data structure.

See also [`SkipList`](@ref), [`PairedSkipNode`](@ref)
