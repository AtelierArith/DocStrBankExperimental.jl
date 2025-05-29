```
vertices_list(cpa::CartesianProductArray)
```

Compute a list of vertices of a (polytopic) Cartesian product of a finite number of sets.

### Input

  * `cpa` – Cartesian product of a finite number of sets

### Output

A list of vertices.

### Algorithm

We assume that the underlying sets are polytopic. Then the high-dimensional set of vertices is just the Cartesian product of the low-dimensional sets of vertices.
