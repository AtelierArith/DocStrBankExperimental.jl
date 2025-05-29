```
l = SkipList{::Type}(; sortedby=identity, skipfactor=2)
l = SkipList{::Type}(elts...; sortedby=identity, skipfactor=2)
```

Create a `SkipList` made of up [SkipNode](@ref)s containing data of a specified type.

The list contains a "dummy" node `head` at the beginning of the list and a "dummy" node `tail` at the end of the list.

The node at the head of the topmost level of the datastructure can be accessed by `l.top`.

The first "real" node of a list `l` can be accessed with `l.head.next` or `head(l)`. Similarly, the last "real" node can be accessed with `l.tail.prev` or `tail(l)`.

The `skipfactor` of the list describes the average number of nodes "skipped" by the above level.

The ordering of the list can be specified by a function, `sortedby`.

See also [`PairedSkipList`](@ref), [`SkipNode`](@ref)
