```
isapplicable(solverType::Type{<:AbstractLinearSolver}, A, x, reg)
```

`solverType`のタイプの`solver`がシステム行列`A`、データ`x`、および正則化項`reg`に適用可能であれば`true`を返します。
