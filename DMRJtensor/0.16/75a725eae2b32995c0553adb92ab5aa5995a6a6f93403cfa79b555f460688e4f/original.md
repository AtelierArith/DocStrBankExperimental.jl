```
Lenv,Renv = makeEnv(psi,mpo[,Lbound=,Rbound=])
```

Generates environment tensors for a MPS (`psi`) with boundaries `Lbound` and `Rbound`

Current environment convention is      LEFT              RIGHT    +–<– 1          3 –-<–+    |                         |    |                         |    +–>– 2          2 –->–+    |                         |    |                         |    +–>– 3          1 –->–+
