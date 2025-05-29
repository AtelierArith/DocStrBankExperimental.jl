Compute an embedding of points by classical multidimensional scaling (MDS). There are two calling options, specified via the required keyword argument `distances`:

```
mds = fit(MDS, X; distances=false, maxdim=size(X,1)-1)
```

`X` is the data matrix. Distances between pairs of columns of `X` are computed using the Euclidean norm. This is equivalent to performing PCA on `X`.

```
mds = fit(MDS, D; distances=true,  maxdim=size(D,1)-1)
```

`D` is a symmetric matrix `D` of distances between points.
