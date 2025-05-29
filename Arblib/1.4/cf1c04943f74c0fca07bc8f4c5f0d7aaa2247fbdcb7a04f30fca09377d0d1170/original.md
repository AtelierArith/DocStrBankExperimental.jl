```
ref(v::Union{ArbVectorOrRef,AcbVectorOrRef}, i)
```

Similar to `v[i]` but instead of an `Arb` or `Acb` returns an `ArbRef` or `AcbRef` which still shares the memory with the `i`-th entry of `v`.
