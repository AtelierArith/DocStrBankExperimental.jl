```
l = PairedSkipList{::Type}(; sortedby=identity, skipfactor=2)
l = PairedSkipList{::Type}(elts...; sortedby=identity, skipfactor=2)
```

Create a `PairedSkipList` with nodes containing data of a specified type. Each node can have an inter-list link to a node belonging to the list's `target`.

The list contains its length `len`, a "dummy" node `head` at the beginning of the list, and a "dummy" node `tail` at the end of the list. The list also contains a reference to its "target" list.

The first "real" node of a list  `l` can be accessed with `l.head.next`. Similarly, the last "real" node can be accessed with `l.tail.prev`.

The `skipfactor` of the list describes the average number of nodes "skipped" by the above level.

The ordering of the list can be specified by a function, `sortedby`.

See also [`SkipList`](@ref), [`PairedSkipNode`](@ref)
