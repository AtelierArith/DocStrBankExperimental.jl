```
evaluate_residual_and_jacobian(system,u;
                               t=0.0, tstep=Inf, embed=0.0, init_dirichlet=false)
```

解の値 u における残差とヤコビ行列を評価します。残差のコピーを含む解ベクトルと、u における線形化のコピーを含む ExendableSparseMatrix を返します。フラグ `init_dirichlet` は、u がシステムによって指定されたディリクレ境界条件を満たすように調整されるべきかどうかを制御します。
