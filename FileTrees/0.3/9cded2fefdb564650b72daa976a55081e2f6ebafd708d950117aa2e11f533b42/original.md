```
values(tree::FileTree; dirs=true)
```

Get a vector of all non-null values from nodes in the tree.

`dirs=false` will exclude any value stored in `FileTree` sub nodes.
