```
hash_position(x::PeriodicVertex{N}, n::Integer) where N
```

Given `x`, a `PeriodicVertex{N}`, and the number `n` of vertex identifiers in a graph, compute a unique positive integer hash for the given vertex.

This hash function is a bijection between the set of all the vertices of the periodic graph and the set of positive integers. Its value is an integer between `1+n*(2d-1)^N` (or `1` if `d == 0`) and `n*(2d+1)^N`, where `d = maximum(abs.(x.ofs))`.

In particular, this means that when one unit cell B is further than another A from the origin (for the Manhattan distance), all vertices in B have a larger hash than all vertices in A.
