```
psi = MPS(type,physindsize,Ns[,regtens=false,oc=1])
```

Constructs `psi` for MPS of tensor type Float64 by making empty tensors of size (1,`physindsize`,1) for w indexing 1:`Ns` (repeats on `physindvec`) with othrogonality center `oc`. `regtens` avoids conversion to `denstens` type (defaulted to perform the conversion for efficiency)
