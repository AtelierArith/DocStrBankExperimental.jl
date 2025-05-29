```
test!(st::WSVarScoreTestInvariant, X1, W1)
```

スコアテストを実行し、時間不変テストデータに対する3つのp値を返します。

# 引数

  * `st::WSVarScoreTestInvariant`: テストのためのデータ構造
  * `X1::Union{Nothing, AbstractMatrix{T}}`: m x r*X1データ、r*X1 == 0の場合はnothing
  * `W1::Union{Nothing, AbstractMatrix{T}}`: m x r*W1データ、r*W1 == 0の場合はnothing
