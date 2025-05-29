```
inf(A::IntervalMatrix{T}) where {T}
```

Return the infimum of an interval matrix `A`, which corresponds to taking the element-wise infimum of `A`.

### Input

  * `A` – interval matrix

### Output

A scalar matrix whose coefficients are the infima of each element in `A`.
