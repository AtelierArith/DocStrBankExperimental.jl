```
factor(a::T) where T <: RingElement -> Fac{T}
```

Return a factorization of $a$ into irreducible elements, as a `Fac{T}`. The irreducible elements in the factorization are pairwise coprime.
