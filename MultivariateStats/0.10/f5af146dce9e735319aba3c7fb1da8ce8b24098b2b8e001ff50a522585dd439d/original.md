(Non)Metric Multidimensional Scaling

Use this class to perform (non)metric multidimensional scaling.

There are two calling options, specified via the required keyword argument `distances`:

```julia
mds = fit(MDS, X; distances=false, maxoutdim=size(X,1)-1)
```

where `X` is the data matrix. Distances between pairs of columns of `X` are computed using the Euclidean norm. This is equivalent to performing PCA on `X`.

```julia
mds = fit(MDS, D; distances=true, maxoutdim=size(D,1)-1)
```

where `D` is a symmetric matrix `D` of distances between points.

In addition, the `metric` parameter specifies type of MDS, By default, it is assigned with `nothing` value which results in performing *metric MDS* with dissimilarities calculated as Euclidean distances.

An arbitrary transformation function can be provided to `metric` parameter to perform metric MDS with transformed proximities. The function has to accept two parameters, a vector of proximities and a vector of distances, corresponding to the proximities, to calculate disparities required for stress calculation. Internally, the proximity and distance vectors are obtained from compact triangular matrix representation of proximity and distance matrices.

For *ratio MDS*, a following ratio transformation function can be used

```julia
mds = fit(MDS, D; distances=true, metric=((p,d)->2 .* p))
```

For *order MDS*, use `isotonic` regression function in the `metric` parameter:

```julia
mds = fit(MDS, D; distances=true, metric=isotonic)
```
