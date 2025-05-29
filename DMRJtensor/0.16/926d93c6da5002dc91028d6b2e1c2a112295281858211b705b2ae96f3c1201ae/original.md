```
Lenv,Renv = makeEnv(dualpsi,psi,mpo[,Lbound=defaultBoundary,Rbound=defaultBoundary,Llabel="Lenv_",Rlabel="Renv_"])
```

Generates environment tensors for a MPS (`psi` and its dual `dualpsi`) with boundaries `Lbound` and `Rbound`; labels `Llabel` and `Rlabel` are for large-types

Current environment convention is      LEFT              RIGHT    +–<– 1          3 –-<–+    |                         |    |                         |    +–>– 2          2 –->–+    |                         |    |                         |    +–>– 3          1 –->–+
