```
invariants(M::QuadSpace)
      -> FieldElem, Dict{AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}, Int}, Vector{Tuple{InfPlc, Int}}
```

Returns a tuple `(n, k, d, H, I)` of invariants of `M`, which determine the isometry class completely. Here `n` is the dimension. The dimension of the kernel is `k`. The element `d` is the determinant of a Gram matrix of the non-degenerate part, `H` contains the non-trivial Hasse invariants and `I` contains for each real place the negative index of inertia.

Note that `d` is determined only modulo squares.
