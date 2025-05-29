```
Coreset()
```

Coreset algorithm implementation, based on "Lucic, Mario & Bachem, Olivier & Krause, Andreas. (2015). Strong Coresets for Hard and Soft Bregman Clustering with Applications to Exponential Family Mixtures."

`Coreset` supports following arguments:

  * `m`: default 100, subsample size
  * `alg`: default `Lloyd()`, algorithm used to clusterize sample

It can be used directly in `kmeans` function

```julia
X = rand(30, 100_000)   # 100_000 random points in 30 dimensions

# 3 clusters, Coreset algorithm with default Lloyd algorithm and 100 subsamples
kmeans(Coreset(), X, 3)

# 3 clusters, Coreset algorithm with Hamerly algorithm and 500 subsamples
kmeans(Coreset(m = 500, alg = Hamerly()), X, 3)
kmeans(Coreset(500, Hamerly()), X, 3)

# alternatively short form can be used for defining subsample size or algorithm only
kmeans(Coreset(500), X, 3) # sample of the size 500, Lloyd clustering algorithm
kmeans(Coreset(Hamerly()), X, 3) # sample of the size 100, Hamerly clustering algorithm
```
