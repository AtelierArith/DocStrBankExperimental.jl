```
RepeatingAffineFEStateMap(
  nblocks::Int,a::Function,l::Vector{<:Function},
  U0,V0,V_φ,U_reg,φh,dΩ...;
  assem_U = SparseMatrixAssembler(U0,V0),
  assem_adjoint = SparseMatrixAssembler(V0,U0),
  assem_deriv = SparseMatrixAssembler(U_reg,U_reg),
  ls::LinearSolver = LUSolver(),
  adjoint_ls::LinearSolver = LUSolver()
)
```

`nblocks`のブロック数、双線形形式`a`、`Function`型の線形形式のベクトル`l`、試行空間`U`とテスト空間`V`、`φh`のためのFE空間`V_φ`、導関数のためのFE空間`U_reg`、および追加の引数としての測度を指定して`RepeatingAffineFEStateMap`のインスタンスを作成します。

オプションの引数により、アセンブラと線形ソルバーの指定が可能です。

# 注意

  * 結果として得られる`FEFunction`は、線形形式のベクトルの各エントリに対応するフィールドを持つ`MultiFieldFEFunction`（またはGridapDistributedの同等物）になります。
