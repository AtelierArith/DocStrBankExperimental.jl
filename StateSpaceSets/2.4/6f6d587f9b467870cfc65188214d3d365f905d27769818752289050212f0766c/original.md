```
Centroid(metric = Euclidean())
```

A distance that can be used in [`set_distance`](@ref). The `Centroid` method returns the distance (according to `metric`) between the [centroids](https://en.wikipedia.org/wiki/Centroid) (a.k.a. centers of mass) of the sets.

`metric` can be any function that takes in two static vectors are returns a positive definite number to use as a distance (and typically is a `Metric` from Distances.jl).
