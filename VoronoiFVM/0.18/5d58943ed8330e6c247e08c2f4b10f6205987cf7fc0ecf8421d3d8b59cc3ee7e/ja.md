```
evaluate_residual_and_jacobian(system,u;
                               t=0.0, tstep=Inf,embed=0.0)
```

解の値 u における残差とヤコビ行列を評価します。残差を含む解ベクトルと、u における線形化を含む ExendableSparseMatrix を返します。
