```
psi = MPS(physindvec[,regtens=false,oc=1,type=Float64])
```

Constructs `psi` for MPS of tensor type `type` by making empty tensors of size (1,`physindvec`[w],1) for w indexing `physindvec` with othrogonality center `oc`. `regtens` avoids conversion to `denstens` type (defaulted to perform the conversion for efficiency)
