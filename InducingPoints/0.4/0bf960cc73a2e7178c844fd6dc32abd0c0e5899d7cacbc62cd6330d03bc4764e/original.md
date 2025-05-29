```
CoverTree(ϵ::Real, lloyds::Bool=true, voronoi::Bool=true, metric::SemiMetric=Euclidean())
```

The CoverTree algorithm [1], recursively builds a tree for which the node will optimally cover the given dataset according to the `metric` distance.

## Arguments:

  * `ϵ::Real`: Spatial resolution. Higher `ϵ` will result in less points.
  * `lloyds::Bool`: Use the centroid of the ball created around the sampled datapoint instead of the datapoint itself if no other inducing point is close
  * `voronoi::Bool`: Reattributes samples to each node at the end of the proecssing of each layer
  * `metric::SemiMetric`: Distance metric used to determine distance between points.

[1] Alexander Terenin, David R. Burt, Artem Artemev, Seth Flaxman, Mark van der Wilk, Carl Edward Rasmussen, Hong Ge: Numerically Stable Sparse Gaussian Processes via Minimum Separation using Cover Trees: https://arxiv.org/abs/2210.07893
