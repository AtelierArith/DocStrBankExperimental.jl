```
neighbors(p::PointCloud, k::Integer)
```

Obtain the indices of the `k` nearest neighbors of each point as a vector of vectors, where the inner vectors have a fixed length `k`.

See also: [`neighbors!`](@ref)
