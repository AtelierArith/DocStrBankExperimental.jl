```
local_clustering(g, v)
local_clustering(g, vs)
```

Return a tuple `(a, b)`, where `a` is the number of triangles in the neighborhood of `v` and `b` is the maximum number of possible triangles. If a list of vertices `vs` is specified, return two vectors representing the number of triangles and the maximum number of possible triangles, respectively, for each node in the list.

This function is related to the local clustering coefficient `r` by $r=\frac{a}{b}$.
