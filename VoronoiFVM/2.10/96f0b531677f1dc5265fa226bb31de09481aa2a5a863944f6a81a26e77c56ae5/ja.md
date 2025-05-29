```
integrate(system,U; boundary=false)
```

領域または境界にわたって解ベクトルを領域ごとに統合します。結果は `nspec x nregion` 行列 $\int_{\Omega_j} U_i\, dx$ または $\int_{\Gamma_j} U_i\, ds$ です。
