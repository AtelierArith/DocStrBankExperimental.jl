```
ref(A::Union{ArbMatrixOrRef,AcbMatrixOrRef}, i, j)
```

Similar to `A[i,j]` but instead of an `Arb` or `Acb` returns an `ArbRef` or `AcbRef` which still shares the memory with the `(i,j)`-th entry of `A`.
