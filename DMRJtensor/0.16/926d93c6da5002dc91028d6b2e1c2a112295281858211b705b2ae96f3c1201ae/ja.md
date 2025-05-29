```
Lenv,Renv = makeEnv(dualpsi,psi,mpo[,Lbound=defaultBoundary,Rbound=defaultBoundary,Llabel="Lenv_",Rlabel="Renv_"])
```

MPS（`psi` とその双対 `dualpsi`）のための環境テンソルを境界 `Lbound` と `Rbound` で生成します。ラベル `Llabel` と `Rlabel` は大きなタイプのためのものです。

現在の環境の規約は      LEFT              RIGHT    +–<– 1          3 –-<–+    |                         |    |                         |    +–>– 2          2 –->–+    |                         |    |                         |    +–>– 3          1 –->–+
