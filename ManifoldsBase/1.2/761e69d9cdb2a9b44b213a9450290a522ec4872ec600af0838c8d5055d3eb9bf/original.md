```
embed_project(M::AbstractManifold, p)
```

Embed `p` from manifold `M` an project it back to `M`. For points from `M` this is identity but in case embedding is defined for points outside of `M`, this can serve as a way to for example remove numerical inaccuracies caused by some algorithms.
