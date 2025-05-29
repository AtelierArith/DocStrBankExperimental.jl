`CholeskyFactorization(; pivot = nothing, tol = 0.0, shift = 0.0, perm = nothing)`

Juliaの組み込み`cholesky`。`cholesky!(A)`を呼び出すのと同等です。

## キーワード引数

  * pivot: デフォルトはNoPivotで、RowMaximumも使用可能です。
  * tol: CHOLMODのtol引数。スパース行列にのみ使用されます。
  * shift: CHOLMODのshift引数。スパース行列にのみ使用されます。
  * perm: CHOLMODのperm引数。スパース行列にのみ使用されます。
