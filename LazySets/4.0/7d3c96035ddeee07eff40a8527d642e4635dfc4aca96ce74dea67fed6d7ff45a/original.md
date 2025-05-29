```
σ(d::AbstractVector,
  R::Rectification{N, <:CartesianProductArray}) where {N}
```

Return a support vector of the rectification of a Cartesian product of a finite number of sets.

### Input

  * `d` – direction
  * `R` – rectification of a Cartesian product of a finite number of sets

### Output

A support vector in the given direction.

### Notes

Note that this implementation creates new `Rectification` objects that do not get preserved. Hence a second support-vector query does not benefit from the computations in the first query. For this use case another implementation should be added.

### Algorithm

Rectification distributes with the Cartesian product. Let $R(·)$ be the rectification of a set. We can just query a support vector for each subspace recursively: $σ_{R(X_1 × ⋯ × X_m)}(d) = σ_{R(X_1)}(d_{X_1}) × ⋯ × σ_{R(X_m)}(d_{X_m})$, where $x × y$ concatenates vectors $x$ and $y$.
