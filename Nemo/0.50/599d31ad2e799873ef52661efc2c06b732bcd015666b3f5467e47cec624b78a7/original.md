```
det_given_divisor(x::ZZMatrix, d::Integer, proved=true)
```

Return the determinant of $x$ given a positive divisor of its determinant. If `proved == true` (the default), the output is guaranteed to be correct, otherwise a heuristic algorithm is used.
