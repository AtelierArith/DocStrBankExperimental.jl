```
community_detection_bethe(g::AbstractGraph, k=-1; kmax=15)
```

Perform detection for `k` communities using the spectral properties of the  Bethe Hessian matrix associated to `g`. If `k` is omitted or less than `1`, the optimal number of communities will be automatically selected. In this case the maximum number of detectable communities is given by `kmax`. Return a vector containing the vertex assignments.

### References

  * [Saade et al.](http://papers.nips.cc/paper/5520-spectral-clustering-of-graphs-with-the-bethe-hessian)
