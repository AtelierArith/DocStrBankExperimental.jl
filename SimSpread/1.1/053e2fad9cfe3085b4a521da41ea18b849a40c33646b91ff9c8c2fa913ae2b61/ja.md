```
construct(y::NamedMatrix, X::NamedMatrix, queries::AbstractVector)
```

*de novo* ネットワークベースの推論予測のためのクエリ-特徴-ソース-ターゲットネットワークを構築し、隣接行列を返します。

# 引数

  * `y::NamedMatrix`: ソース-ターゲット二部ネットワークの隣接行列
  * `X::NamedMatrix`: ソース-特徴二部隣接行列
  * `queries::AbstractVector`: クエリとして使用するソースノード

# 拡張ヘルプ

この実装は k-分割または一つを除く交差検証を目的としています。
