```
fit(MDS, X; kwargs...)
```

Compute an embedding of `X` points by classical multidimensional scaling (MDS). There are two calling options, specified via the required keyword argument `distances`:

```
mds = fit(MDS, X; distances=false, maxoutdim=size(X,1)-1)
```

where `X` is the data matrix. Distances between pairs of columns of `X` are computed using the Euclidean norm. This is equivalent to performing PCA on `X`.

```
mds = fit(MDS, D; distances=true, maxoutdim=size(D,1)-1)
```

where `D` is a symmetric matrix `D` of distances between points.
