```
construct(ytrain::T, ytest::T, Xtrain::T, Xtest::T) where {T<:NamedMatrix}
```

*de novo* ネットワークベースの推論予測のためのクエリ-フィーチャー-ソース-ターゲットネットワークを構築し、隣接行列を返します。

# 引数

  * `ytrain::NamedMatrix` : トレーニングソース-ターゲット二部グラフ隣接行列
  * `ytest::NamedMatrix` : テストソース-ターゲット二部グラフ隣接行列
  * `Xtrain::NamedMatrix` : トレーニングソース-フィーチャー二部グラフ隣接行列
  * `Xtest::NamedMatrix` : テストソース-フィーチャー二部グラフ隣接行列

# 拡張ヘルプ

この実装は、時間分割交差検証またはクエリネットワークの手動構築を目的としています。
