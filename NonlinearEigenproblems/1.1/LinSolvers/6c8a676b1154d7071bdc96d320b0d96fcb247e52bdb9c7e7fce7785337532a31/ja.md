```
FactorizeLinSolverCreator(;umfpack_refinements,max_factorizations,nep,precomp_values)
```

`FactorizeLinSolverCreator`オブジェクトは、`create_linsolver`関数を介して`FactorizeLinSolver`オブジェクトをインスタンス化できます。

`FactorizeLinSolver`は`factorize`呼び出しに基づいています。`factorize`への呼び出しのタイミングは、`FactorizeLinSolverCreator`へのパラメータによって制御できます：

  * デフォルトでは、`factorize`呼び出しは`FactorizeLinSolver`のインスタンス化によって実行されます。つまり、NEPソルバーが`create_linsolver`を呼び出すときです。
  * また、`FactorizeLinSolverCreator`をインスタンス化するタイミングで因数分解を事前に計算することもできます。`precomp_values::Vector{Number}`を空でないベクターに設定し、`nep`キーワード引数を設定すると、`FactorizeLinSolverCreator`がインスタンス化されるときに`precomp_values`内のすべてのλ値の因数分解が計算されます。NEPソルバーがそのベクターからのλ値で`create_linsolver`を呼び出すと、因数分解が使用されます（そうでなければ計算されます）。

さらなる再利用が可能です。変数`max_factorizations`が正の値に設定されている場合、そのオブジェクトは再利用のためにその数の因数分解を保存します。すべての`lin_solve`呼び出しは、以前にその`λ`のために計算された`lin_solve`呼び出しがない限り、因数分解を計算します。この手順は最大で`max_factorization`を保存できます（`Inf`に設定できます）。

参照：[`FactorizeLinSolver`](@ref), [`create_linsolver`](@ref)
