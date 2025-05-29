```
fastest_exact(::CombinatorialInstance)
```

Returns the overall fastest algorithm to solve the combinatorial instance (i.e. this function returns a `CombinatorialAlgorithm` instance). If no such  algorithm is known, then the return value is `nothing` (for instance, there is  no algorithm that is always faster than the others). The returned algorithm is always exact, and never approximate.
