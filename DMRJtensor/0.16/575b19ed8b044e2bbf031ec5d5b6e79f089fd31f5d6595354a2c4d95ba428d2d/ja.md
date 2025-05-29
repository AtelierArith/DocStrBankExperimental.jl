```
Lbound = makeBoundary(dualpsi,psi,mpovec...[,left=true,rightind=3])
```

入力MPS `psi`、双MPS `dualpsi`、および任意の数のMPO `mpovec`から境界テンソル`Lbound`を作成します。`left`は左または右の境界テンソルを作成するかどうかを制御し、`rightind`は右リンクインデックスに対応するMPSの番号インデックスです。

#注意:

  * 密なテンソルは単にones(1,1,1,...)

現在の環境の規約は      LEFT              RIGHT    +–<– 1          3 –-<–+    |                         |    |                         |    +–>– 2          2 –->–+    |                         |    |                         |    +–>– 3          1 –->–+

参照: [`makeEnds`](@ref)
