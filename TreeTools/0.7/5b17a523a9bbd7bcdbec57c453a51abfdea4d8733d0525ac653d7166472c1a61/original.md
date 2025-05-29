```
lca(i_node::TreeNode, j_node::TreeNode)
```

Find and return lowest common ancestor of `i_node` and `j_node`. Idea is to go up in the tree in an asymmetric way on the side of the deeper node, until both are at equal distance from root. Then, problem is solved by going up in a symmetric way. (https://stackoverflow.com/questions/1484473/how-to-find-the-lowest-common-ancestor-of-two-nodes-in-any-binary-tree/6183069#6183069)
