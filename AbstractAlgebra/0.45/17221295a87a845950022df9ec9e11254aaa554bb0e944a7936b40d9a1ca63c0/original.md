```
scalar_matrix(R::NCRing, n::Int, a::NCRingElement)
scalar_matrix(n::Int, a::NCRingElement)
```

Return the $n \times n$ matrix over `R` with `a` along the main diagonal and zeroes elsewhere. If `R` is not specified, it defaults to `parent(a)`.
