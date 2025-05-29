```
minimum_pairwise_distance(X::StateSpaceSet, kdtree = dimension(X) < 10, metric = Euclidean())
```

Return `min_d, min_pair`: the minimum pairwise distance of all points in the dataset, and the corresponding point pair. The third argument is a switch of whether to use KDTrees or a brute force search.
