```
BatchIterator(X; batchsize = nothing, limit=size(X,2))
```

Wrapper allowing to iterate over batches of `batchsize` columns of `X`. `X` can be of any type supporting `size` and 2d indexing. When `limit` is provided, iteration is restricted to the columns of `X[:, 1:limit]`.
