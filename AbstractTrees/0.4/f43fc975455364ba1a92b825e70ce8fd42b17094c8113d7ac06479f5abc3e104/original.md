```
isroot(x)
```

Whether `x` is the absolute root of a tree.  More specifically, this returns `true` if `parent(x) ≡ nothing`, or `parent(root, x) ≡ nothing`.  That is, while any node is the root of some tree, this function only returns true for nodes which have parents which cannot be obtained with the `AbstractTrees` interface.
