```
σ(d::AbstractVector, R::Rectification{N, <:CartesianProduct}) where {N}
```

Return a support vector of the rectification of a Cartesian product of two sets.

### Input

  * `d` – direction
  * `R` – rectification of a Cartesian product of two sets

### Output

A support vector in the given direction.

### Notes

Note that this implementation creates new `Rectification` objects that do not get preserved. Hence a second support-vector query does not benefit from the computations in the first query. For this use case another implementation should be added.

### Algorithm

Rectification distributes with the Cartesian product. Let $R(·)$ be the rectification of a set. We can just query a support vector for $R(X)$ and $R(Y)$ recursively: $σ_{R(X × Y)}(d) = σ_{R(X)}(d_X) × σ_{R(Y)}(d_Y)$, where $x × y$ concatenates vectors $x$ and $y$.
