```
htensor(tree,trten,fmat)
htensor(tree,trten,U1,U2,...)
```

Hierarchical Tucker tensor.

## Arguments:

  * `tree::dimtree`: Dimension tree.
  * `trten::TensorCell`: Transfer tensors. One for each internal node of the tree.
  * `fmat::MatrixCell`: Frame matrices. One for each leaf of the tree.

For htensor X, X.isorth=true if frame matrices are othonormal.
