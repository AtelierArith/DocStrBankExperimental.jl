```
graft!(tree::Tree, n, r; graft_on_leaf=false, time=branch_length(n))
```

Graft `n` onto `r` and return the grafted node. `r` can be a label or a `TreeNode`, and should belong to `tree`. `n` can be a `TreeNode` or a `Tree`. In the latter case, `n` will be *copied* before being grafted. None of the nodes of the subtree of `n` should belong to `tree`.

If `r` is a leaf and `graft_on_leaf` is set to `false` (default), will raise an error.
