```
isdescendant(node1, node2; equiv=(≡))
```

Check if `node1` is a descendant of `node2`. This isequivalent to checking whether `node1` is a member of the subtree rooted at `node2` (see [`intree`](@ref)) except that a node cannot be a descendant of itself.

Internally this calls `intree(node1, node2)` and so may be slow if a specialized method of that function is not available.

Equivalence is established with the `equiv` function.  Note that new methods should also define `equiv` or calls may fall back to the default method.
