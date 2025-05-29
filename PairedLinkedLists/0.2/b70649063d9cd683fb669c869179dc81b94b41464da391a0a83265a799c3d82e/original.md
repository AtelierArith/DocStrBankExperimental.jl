```
removetarget!(node)
```

Remove the link between the node or list and its target (if the object is already paired) and return `node`.

If the object is a `PairedListNode` or `PairedLinkedList`, the link will be deleted from both the object and its target.

If the object is a `TargetedListNode` or `PairedLinkedList`, the link will be deleted from only the object.

See also [`hastarget`](@ref), [`addtarget!`](@ref)
