```
psi = applyOps!(psi,sites,Op[,trail=ones(1,1)])
```

Applies operator `Op` (any `TensType`) in-place to the MPS `psi` at sites `sites`, a vector of integers. A trailing operator `trail` can be applied if not the default.
