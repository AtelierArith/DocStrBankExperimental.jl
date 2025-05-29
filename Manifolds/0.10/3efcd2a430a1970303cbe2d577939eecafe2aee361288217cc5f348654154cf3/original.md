```
local_metric(M::Sphere{n}, p, ::DefaultOrthonormalBasis)
```

return the local representation of the metric in a [`DefaultOrthonormalBasis`](@extref `ManifoldsBase.DefaultOrthonormalBasis`), namely the diagonal matrix of size $n×n$ with ones on the diagonal, since the metric is obtained from the embedding by restriction to the tangent space $T_p\mathcal M$ at $p$.
