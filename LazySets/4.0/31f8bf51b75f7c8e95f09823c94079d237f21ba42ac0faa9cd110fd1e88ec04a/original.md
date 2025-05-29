```
tosimplehrep(S::LazySet)
```

Return the simple constraint representation $Ax ≤ b$ of a polyhedral set from its list of linear constraints.

### Input

  * `S` – polyhedral set

### Output

The tuple `(A, b)` where `A` is the matrix of normal directions and `b` is the vector of offsets.

### Algorithm

This fallback implementation relies on `constraints_list(S)`.
