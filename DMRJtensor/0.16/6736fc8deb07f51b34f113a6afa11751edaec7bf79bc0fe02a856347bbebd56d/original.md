```
psi = MPS(T,A[,regtens=false,oc=1])
```

Constructs `psi` for MPS of tensor type `T` with tensors `A` (Array of tensors or MPS) with orthogonality center `oc`. `regtens` avoids conversion to `denstens` type (defaulted to perform the conversion for efficiency)
