```
trim_tree_once!(net::Network)
```

A support function for `trim_tree!`, `trim_tree_once!` removes all the empty leaf busses. When trimming the tree sometimes new leafs are created. So `trim_tree!` loops over `trim_tree_once!`.
