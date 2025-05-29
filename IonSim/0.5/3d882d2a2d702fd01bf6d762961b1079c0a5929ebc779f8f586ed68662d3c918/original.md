```
groundstate(obj)
```

If obj is a `VibrationalMode`, returns the N=0 ket of that mode. If obj is a Vector of `VibrationalMode`, returns a tensor product `mode1[0] ⊗ mode2[0] ⊗ ...` in the same order given. If obj is a `LinearChain`, returns the full ground state of the motional degrees of freedom as a tensor product.
