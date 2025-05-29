```
Lenv,Renv = makeEnv(psi,mpo[,Lbound=,Rbound=])
```

MPS（`psi`）のための環境テンソルを境界 `Lbound` と `Rbound` で生成します。

現在の環境の規約は      LEFT              RIGHT    +–<– 1          3 –-<–+    |                         |    |                         |    +–>– 2          2 –->–+    |                         |    |                         |    +–>– 3          1 –->–+
