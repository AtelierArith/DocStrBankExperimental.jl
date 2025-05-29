```
multiphase_edge_variable_container(; default::DefaultType=missing)
```

デフォルトの型が `missing` の `DefaultDict` の `DefaultDict` を返します。変数をインデックス付けするための3つのキータイプは次のとおりです。

1. `Tuple{String, String}` エッジ名用
2. `Int` タイムステップ用
3. `AbstractVecOrMat` フェーズ変数のベクトルまたは行列用
