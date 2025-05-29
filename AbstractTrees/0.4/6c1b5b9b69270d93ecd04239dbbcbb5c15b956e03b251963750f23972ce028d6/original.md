```
getdescendant(node, idx)
```

Obtain a node from a tree by indexing each level of the tree with the elements of `idx`.

This function is defined for all trees regardless of whether they have the [`IndexedChildren`](@ref). This is because a tree without [`IndexedChildren`](@ref) might have special cases in which all children are indexable, a prominent example being `Array` which may not have indexable sub-trees (e.g. an array containing a Dict) but there are common special cases in which array trees are fully indexable (e.g. a tree in which every non-leaf node is an array).

The elements of `idx` can be any argument to `getindex`, not necessarily integers.  For example, `getdescendant(Dict("a"=>1), ("a",))` returns `1`.

Note that this is a separate concept from indexed trees which by default do not have `IndexedChildren()`, see [`IndexNode`](@ref).

## Example

```julia
v = [1, [2, [3, 4]]]

getdescendant(v, (2, 2, 1)) == 3
```
