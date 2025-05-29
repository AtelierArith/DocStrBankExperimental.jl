```
laplacian_symm!(v,w)
```

Evaluate the symmetric 5-point discrete Laplacian of `w` and return it as `v`. The data `w` can be of type dual nodes only for now. This symmetric Laplacian also evaluates the partial Laplacians (using only available stencil data) on the ghost nodes.
