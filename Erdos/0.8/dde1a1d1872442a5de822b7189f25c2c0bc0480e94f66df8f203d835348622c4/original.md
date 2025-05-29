```
community_detection_bethe(g::AGraph, k=-1; kmax=15)
```

Community detection using the spectral properties of the Bethe Hessian matrix associated to `g` (see [Saade et al.](http://papers.nips.cc/paper/5520-spectral-clustering-of-graphs-with-the-bethe-hessian)). `k` is the number of communities to detect. If omitted or if `k < 1` the optimal number of communities will be automatically selected. In this case the maximum number of detectable communities is given by `kmax`. Returns a vector containing the vertex assignments.
