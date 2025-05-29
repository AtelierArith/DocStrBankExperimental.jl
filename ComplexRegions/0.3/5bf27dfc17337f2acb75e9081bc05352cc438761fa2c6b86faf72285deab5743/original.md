```
vertex(P::AbstractPath,k::Integer)
```

Return the `k`th vertex of the path `P`. The index is applied circularly; e.g, if the closed path has n curves, then ...,1-n,1,1+n,... all refer to the first vertex.
