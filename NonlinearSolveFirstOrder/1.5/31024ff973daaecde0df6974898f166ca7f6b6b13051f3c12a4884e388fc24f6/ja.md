```
NewtonRaphson(;
    concrete_jac = nothing, linsolve = nothing, linesearch = missing,
    autodiff = nothing, vjp_autodiff = nothing, jvp_autodiff = nothing
)
```

スパース行列の効率的な処理をサポートするために、色付き自動微分と前処理された線形ソルバーを使用した高度なNewtonRaphson実装。大規模で数値的に困難な非線形システムのために設計されています。
