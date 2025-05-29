```
node2tree(root::TreeNode{T}; label = default_tree_label(), force_new_labels=false)
```

Create a `Tree` object from `root` with name `label`. If `force_new_labels`, a random string is added to node labels to make them unique.
