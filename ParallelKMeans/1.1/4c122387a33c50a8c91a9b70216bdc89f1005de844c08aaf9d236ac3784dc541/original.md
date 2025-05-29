```
Yinyang()
```

Yinyang algorithm implementation, based on "Yufei Ding et al. 2015. Yinyang K-Means: A Drop-In Replacement of the Classic K-Means with Consistent Speedup. Proceedings of the 32nd International Conference on Machine Learning, ICML 2015, Lille, France, 6-11 July 2015"

Generally it outperform `Hamerly` algorithm and has roughly the same time as `Elkan` algorithm with much lower memory consumption.

`Yinyang` supports following arguments: `auto`: `Bool`, indicates whether to perform automated or manual grouping `group_size`: `Int`, estimation of average number of clusters per group. Lower numbers corresponds to higher calculation speed and higher memory consumption and vice versa.

It can be used directly in `kmeans` function

```julia
X = rand(30, 100_000)   # 100_000 random points in 30 dimensions

# 3 clusters, Yinyang algorithm, with deault 7 group_size
kmeans(Yinyang(), X, 3)

# Following are equivalent
# 3 clusters, Yinyang algorithm with 10 group_size
kmeans(Yinyang(group_size = 10), X, 3)
kmeans(Yinyang(10), X, 3)

# One group with the size of the number of points
kmeans(Yinyang(auto = false), X, 3)
kmeans(Yinyang(false), X, 3)

# Chinese writing can be used
kmeans(阴阳(), X, 3)
```
