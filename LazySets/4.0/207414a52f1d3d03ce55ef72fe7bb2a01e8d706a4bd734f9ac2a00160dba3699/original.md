```
constraints_list(ms::MinkowskiSum)
```

Return a list of constraints of the Minkowski sum of two polyhedral sets.

### Input

  * `ms` – Minkowski sum of two polyhedral sets

### Output

The list of constraints of the Minkowski sum.

### Algorithm

We compute a concrete set representation via `minkowski_sum` and call `constraints_list` on the result.
