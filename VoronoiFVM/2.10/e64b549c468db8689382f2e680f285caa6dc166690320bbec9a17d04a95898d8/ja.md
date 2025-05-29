```
integrate(system,F,U; boundary=false, data=system.physics.data)
```

ノード関数 `F` を解ベクトル `U` に対して、領域ごとにドメインまたは境界上で統合します。結果は `nspec x nregion` 行列 $\int_{\Omega_j} F_i(U)\, dx$ または $\int_{\Gamma_j} F_i(U)\, ds$ です。
