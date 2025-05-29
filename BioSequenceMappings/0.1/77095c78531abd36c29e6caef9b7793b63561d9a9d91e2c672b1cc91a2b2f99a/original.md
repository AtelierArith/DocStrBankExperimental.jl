```
pairwise_frequencies(X::AbstractAlignment, w=X.weights; as_mat=false)
```

Return a `q x q x L x L` tensor. The `(a, b, i, j)` element is the fraction of sequences for which we see `a` at position `i` and `b` at position `j`.

If `as_mat=true`, will return a `qL x qL` matrix, with `q x q` blocks representing correlations between two specific columns.
