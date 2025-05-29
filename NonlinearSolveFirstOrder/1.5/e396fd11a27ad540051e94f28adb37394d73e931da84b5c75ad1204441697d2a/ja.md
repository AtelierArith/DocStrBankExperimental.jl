```
GaussNewton(;
    concrete_jac = nothing, linsolve = nothing, linesearch = missing,
    autodiff = nothing, vjp_autodiff = nothing, jvp_autodiff = nothing
)
```

スパース行列の効率的な処理をサポートする高度なGaussNewton実装で、色分け自動微分と前処理された線形ソルバーを利用しています。大規模で数値的に困難な非線形システムのために設計されています。
