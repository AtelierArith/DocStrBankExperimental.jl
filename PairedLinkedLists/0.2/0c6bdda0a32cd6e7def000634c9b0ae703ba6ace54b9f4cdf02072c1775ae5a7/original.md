```
l = DoublyLinkedList{::Type}()
l = DoublyLinkedList(elts...)
```

Create a `DoublyLinkedList` made up of [`ListNode`](@ref)s with with nodes containing data of a specified type.

The list contains its length `len`, a "dummy" node `head` at the beginning of the list, and a "dummy" node `tail` at the end of the list . 

The first "real" node of a list `l` can be accessed with `l.head.next` or `head(l)`. Similarly, the last "real" node can be accessed with `l.tail.prev` or `tail(l)`.

See also [`ListNode`](@ref), [`SkipList`](@ref), [`PairedLinkedList`](@ref), [`TargetedLinkedList`](@ref)
