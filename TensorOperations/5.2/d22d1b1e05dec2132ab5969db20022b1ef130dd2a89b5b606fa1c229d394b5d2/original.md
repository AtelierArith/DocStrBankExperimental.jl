```
checkcontractible(A, iA, conjA, B, iB, conjB, label)
```

Verify whether two tensors `opA(A)` and `opB(B)` are compatible for having their respective index `iA` and `iB` contracted, and throws an error if not. The operation `opA` acts as `identity` if `conjA` equals `false` and as `conj` if `conjA` equals `true`; the operation `opB` is determined by `conjB` analogously.
