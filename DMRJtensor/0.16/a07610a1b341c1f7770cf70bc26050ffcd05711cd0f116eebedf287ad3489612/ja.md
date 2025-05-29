```
Lenv,Renv = makeEnds(psi[,mpovec,Lbound=,Rbound=])
```

与えられた可変MPOのシステムに対して最初と最後の環境テンソルを生成します。他の実装と同じですが、`dualpsi`=`psi`です。

# 引数:

  * `psi::MPS`: MPS
  * `mpovec::MPO`: MPOs
  * `Lbound::TensType`: 左境界
  * `Rbound::TensType`: 右境界

現在の環境の規約は      LEFT              RIGHT    +–<– 1          3 –-<–+    |                         |    |                         |    +–>– 2          2 –->–+    |                         |    |                         |    +–>– 3          1 –->–+
