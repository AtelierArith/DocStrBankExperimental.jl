```
l = PairedLinkedList{::Type}()
l = PairedLinkedList{::Type}(elts...)
```

Create a `PairedLinkedList` made up of [`PairListNode`](@ref)s containing data of a specified type. Each node can have an inter-list link to a node belonging to the list's `target`.

The list contains its length `len`, a "dummy" node `head` at the beginning of the list, and a "dummy" node `tail` at the end of the list . 

The first "real" node of a list `l` can be accessed with `l.head.next` or `head(l)`. Similarly, the last "real" node can be accessed with `l.tail.prev` or `tail(l)`.

See also [`PairedListNode`](@ref), [`PairedSkipList`](@ref), [`DoublyLinkedList`](@ref), [`TargetedLinkedList`](@ref)
