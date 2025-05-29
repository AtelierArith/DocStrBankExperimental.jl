```
check_tree(t::Tree; strict=true)
```

  * Every non-leaf node should have at least one child (two if `strict`)
  * Every non-root node should have exactly one ancestor
  * If n.child[...] == c, c.anc == n is true
  * Tree has only one root
