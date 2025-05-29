```
conjugates_arb_real(x::AbsSimpleNumFieldElem, abs_tol::Int) -> Vector{ArbFieldElem}
```

Compute the real conjugates of $x$ as elements of type `ArbFieldElem`.

Every entry $y$ of the array returned satisfies `radius(y) < 2^-abs_tol`.
