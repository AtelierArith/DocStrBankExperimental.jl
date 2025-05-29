`CHOLMODFactorization(; shift = 0.0, perm = nothing)`

CHOLMODのポリアルゴリズムのラッパーで、コレスキー分解とldltを混合しています。パフォーマンスのためにコレスキーを試み、条件付けが原因でコレスキーが失敗した場合はldltを再試行します。

スパース行列のみをサポートしています。

## キーワード引数

  * shift: CHOLMODのシフト引数。
  * perm: CHOLMODのperm引数。
