```
vertices_list(ms::MinkowskiSum)
```

Return a list of vertices for the Minkowski sum of two sets.

### Input

  * `ms` – Minkowski sum of two sets

### Output

A list of vertices of the Minkowski sum of two sets.

### Algorithm

We compute the concrete Minkowski sum (via `minkowski_sum`) and call `vertices_list` on the result.
