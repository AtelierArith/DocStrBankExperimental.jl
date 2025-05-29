`CHOLMODFactorization(; shift = 0.0, perm = nothing)`

CHOLMODのポリアルゴリズムのラッパーで、Cholesky因子分解とldltを混合しています。性能のためにCholeskyを試み、条件付けが原因でCholeskyが失敗した場合はldltを再試行します。

スパース行列のみをサポートしています。

## キーワード引数

  * shift: CHOLMODのシフト引数。
  * perm: CHOLMODのperm引数。
