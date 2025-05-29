```
Neighborhood(; logbase=2, minsize=2, filter=SatNeighborhood())
```

Determines the size of the neighborhood, $k$ is adjusted as a callback, and it is intended to affect previously inserted vertices. The neighborhood is designed to consider two components $k=in+out$, i.e. *in*coming and *out*going edges for each vertex.

  * The $out$ size is computed as $minsize + \log(logbase, n)$ where $n$ is the current number of indexed elements; this is computed searching

for $out$  elements in the current index.

  * The $in$ size is unbounded.
  * filter is intended to postprocess neighbors (after search process, i.e., once out edges are computed); do not change $k$ but always must return a copy of the filterd result set.

Note: Set $logbase=Inf$ to obtain a fixed number of $in$ nodes; and set $minsize=0$ to obtain a pure logarithmic growing neighborhood.
