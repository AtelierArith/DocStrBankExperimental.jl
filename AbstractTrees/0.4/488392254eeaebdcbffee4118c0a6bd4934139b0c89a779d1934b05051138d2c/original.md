```
intree(node, root; equiv=(≡))
```

Check if `node` is a member of the tree rooted at `root`.

By default this traverses through the entire tree in search of `node`, and so may be slow if a more specialized method has not been implemented for the given tree type.

Equivalence is established with the `equiv` function.  Note that new methods should also define `equiv` or calls may fall back to the default method.

See also: [`isdescendant`](@ref)
