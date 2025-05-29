```
psi = MPS(A[,regtens=false,oc=psi.oc,type=...])
```

Constructs `psi` for MPS with tensors `A` (Array of tensors or MPS) with orthogonality center `oc`. `regtens` avoids conversion to `denstens` type (defaulted to perform the conversion for efficiency); `type` defaults to the input type of the tensors in `psi`
