```
ρ(d::AbstractVector, cap::Intersection)
```

Return an upper bound on the support function of the intersection of two sets in a given direction.

### Input

  * `d`   – direction
  * `cap` – intersection of two sets

### Output

An upper bound on the support function in the given direction.

### Algorithm

The support function of an intersection of $X$ and $Y$ is upper-bounded by the minimum of the support-function evaluations for $X$ and $Y$.
