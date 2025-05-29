```
score(metric::Symbol, actual::Vector, predicted::Vector)
```

学習者の予測を真の値と比較してスコアを計算します。

利用可能なメトリック：

  * :accuracy
  * `metric`: 評価に使用するメトリック
  * `actual`: 真の値
  * `predicted`: 予測値

返り値: 学習者のスコア
