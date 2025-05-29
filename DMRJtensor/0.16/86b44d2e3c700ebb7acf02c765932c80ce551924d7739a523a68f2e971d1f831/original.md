```
newpsi = applyMPO(psi,H...[,m=1,cutoff=0.])
```

Applies MPOs (`H`) to an MPS (`psi`) and truncates to maximum bond dimension `m` and cutoff `cutoff`. Not recommended except for small problems since bond dimension is not truncated uniformly.
