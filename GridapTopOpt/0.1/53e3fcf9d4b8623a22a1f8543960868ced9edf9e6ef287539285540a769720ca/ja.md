```
NonlinearFEStateMap(
  res::Function,U,V,V_φ,U_reg,φh,dΩ...;
  assem_U = SparseMatrixAssembler(U,V),
  assem_adjoint = SparseMatrixAssembler(V,U),
  assem_deriv = SparseMatrixAssembler(U_reg,U_reg),
  nls::NonlinearSolver = NewtonSolver(LUSolver();maxiter=50,rtol=1.e-8,verbose=true),
  adjoint_ls::LinearSolver = LUSolver()
)
```

`res`を`Function`型として、試行空間`U`とテスト空間`V`、`φh`のためのFE空間`V_φ`、導関数のためのFE空間`U_reg`、および追加の引数として測度を指定して`NonlinearFEStateMap`のインスタンスを作成します。

オプションの引数により、アセンブラ、非線形ソルバー、および随伴（線形）ソルバーを指定できます。
