```
factor_squarefree(a::T) where T <: RingElement -> Fac{T}
```

Return a factorization of $a$ into squarefree elements, as a `Fac{T}`. The squarefree elements in the factorization are pairwise coprime.
