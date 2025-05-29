```
embed_project(M::AbstractManifold, p, X)
```

Embed vector `X` tangent at `p` from manifold `M` an project it back to tangent space at `p`. For points from that tangent space this is identity but in case embedding is defined for tangent vectors from outside of it, this can serve as a way to for example remove numerical inaccuracies caused by some algorithms.
