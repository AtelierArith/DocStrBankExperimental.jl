```
addtarget!(node, target_node)
addtarget!(list, target_list)
```

Add a link between a the provided node or list and another object of the same type to be assigned its `target`. 

If the first object is a `PairedListNode' or a 'PairedLinkedList' and either object previously had a target, the prior link is removed.

If the first object is a `TargetedListNode` or a `TargetedLinkedList`, the second object remains unchanged.

See also [`hastarget`](@ref), [`removetarget!`](@ref)
