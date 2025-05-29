```
farthest_points_sample(
    X::PointCloud, n::Integer; 
    metric = Euclidean()
    )
```

Given `X` and an integer `n`, return a subset of `X` such that its points are the most distant possible from each other.

## Details

Let `X` be a metric space with `k` points. Select a random point `x_1` ∈ `X`. Select then `x_2` as the point most distant from `x_1` in relation to the given metric. After that, choose `x_3` as the point most distant to both `x_1` and `x_2` at the same time. Keep choosing points like this until we have `n` points.
