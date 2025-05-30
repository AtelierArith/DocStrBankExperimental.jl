```
r2(model::StatisticalModel, variant::Symbol)
r²(model::StatisticalModel, variant::Symbol)
```

擬似決定係数（擬似 R²）。

非線形モデルの場合、いくつかの擬似 R² 定義の中から `variant` を介して選択する必要があります。サポートされているバリアントは次のとおりです。

  * `:MacFadden`（別名：尤度比指数）、定義は $1 - \log (L)/\log (L_0)$;
  * `:CoxSnell`、定義は $1 - (L_0/L)^{2/n}$;
  * `:Nagelkerke`、定義は $(1 - (L_0/L)^{2/n})/(1 - L_0^{2/n})$。
  * `:devianceratio`、定義は $1 - D/D_0$。

上記の式において、$L$ はモデルの尤度、$L_0$ は帰無モデル（切片のみのモデル）の尤度、$D$ はモデルの逸脱度（飽和モデルからの）、$D_0$ は帰無モデルの逸脱度、$n$ は観測数（[`nobs`](@ref) によって与えられる）です。

Cox-Snell と逸脱比のバリアントは、線形モデルに対する R² の古典的定義と一致します。
