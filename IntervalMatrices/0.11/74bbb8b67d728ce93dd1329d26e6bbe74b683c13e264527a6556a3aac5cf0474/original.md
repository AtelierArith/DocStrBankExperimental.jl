```
midpoint_radius(A::IntervalMatrix{T}) where {T}
```

Split an interval matrix $A$ into two scalar matrices $C$ and $S$ such that $A = C + [-S, S]$.

### Input

  * `A` – interval matrix

### Output

A pair `(C, S)` such that the entries of `C` are the central points and the entries of `S` are the (nonnegative) radii of the intervals in `A`.
