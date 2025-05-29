```
knn!(idxs, dists, tree, point, k)
```

Same functionality as `knn` but stores the results in the input vectors `idxs` and `dists`. Useful if one want to avoid allocations or specify the element type of the output vectors.

See also: `knn`, `nn`.
