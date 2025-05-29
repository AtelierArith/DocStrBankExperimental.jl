```
order(A::AbstractAssociativeAlgebra{QQFieldElem}, M::QQMatrix; check::Bool = true,
      cached::Bool = true)
  -> AlgAssAbsOrd
```

Returns the order of $A$ with basis matrix $M$. If `check` is set, it is checked whether $M$ defines an order.
