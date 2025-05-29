```
integrate(system,F, Ut; boundary=false, data=system.physics.data)
```

領域ごとにドメインまたは境界で過渡解ベクトルを統合します。結果は `nspec x nregion x nsteps` の DiffEqArray $\int_{\Omega_j} F_i(U_k)\, dx$ または $\int_{\Gamma_j} F_i(U_k)\, ds$ です。
