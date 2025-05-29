```
AffineFEStateMap(
  a::Function,l::Function,
  U,V,V_φ,U_reg,φh,dΩ...;
  assem_U = SparseMatrixAssembler(U,V),
  assem_adjoint = SparseMatrixAssembler(V,U),
  assem_deriv = SparseMatrixAssembler(U_reg,U_reg),
  ls::LinearSolver = LUSolver(),
  adjoint_ls::LinearSolver = LUSolver()
)
```

`a` および `l` を `Function` 型として、試行空間 `U` とテスト空間 `V`、`φh` のための FE 空間 `V_φ`、導関数のための FE 空間 `U_reg`、および追加の引数として測度を指定して `AffineFEStateMap` のインスタンスを作成します。

オプションの引数により、アセンブラと線形ソルバーを指定できます。
