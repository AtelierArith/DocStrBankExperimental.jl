```
Lenv,Renv = makeEnds(dualpsi,psi[,mpovec,Lbound=,Rbound=])
```

与えられた変数MPOのシステムのための最初と最後の環境を生成します

# 引数:

  * `dualpsi::MPS`: 双対MPS
  * `psi::MPS`: MPS
  * `mpovec::MPO`: MPO
  * `Lbound::TensType`: 左境界
  * `Rbound::TensType`: 右境界

現在の環境の規約は      LEFT              RIGHT    +–<– 1          3 –-<–+    |                         |    |                         |    +–>– 2          2 –->–+    |                         |    |                         |    +–>– 3          1 –->–+
