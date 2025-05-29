```
build_loss_function(eqs, indvars, depvars, phi, derivative, init_params;
    bc_indvars=nothing)
```

主方程または境界条件の実行可能なJulia関数である損失関数の本体を返します。
