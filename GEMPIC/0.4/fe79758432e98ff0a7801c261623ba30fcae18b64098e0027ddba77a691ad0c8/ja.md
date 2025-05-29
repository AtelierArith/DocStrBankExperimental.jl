```
HamiltonianSplitting( maxwell_solver,
                      kernel_smoother_0, kernel_smoother_1,
                      particle_group, e_dofs, b_dofs)
```

Vlasov-Maxwellのためのハミルトニアン分割タイプ

  * 各区間でのスプライン関数の積分（次数p+1）
  * 各区間でのスプライン関数の積分（次数p）
  * 電場の2つの成分を表す`e_dofs`
  * 磁場を表す`b_dofs`
  * 電流密度のカーネル表現のための`j_dofs`。
