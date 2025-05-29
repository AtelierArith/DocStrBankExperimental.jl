```
weight_kernel!(coeff_terms, log_e_1_terms, log_e_2_terms, φ_old, Ψ, y_t,
    s_t_nontemp, det_HH, inv_HH; initialize = false,
    poolmodel = false)
```

weight_kernel関数の出力は、適応的なφの探索を加速することを目的としており、ルート解法アルゴリズムの各反復で同じ行列乗算ステップを行わないようにしています。

指数項は最初にログされ、その後、増分重み計算で指数化されるため、問題は良好に条件付けされています（すなわち、非常に大きな負の数を指数化しない）。

この関数は`coeff_terms`、`log_e_1_terms`、および`log_e_2_terms`を修正します。
