```
(classifier::TrainedClassifier)(
    index::AbstractDocumentIndex; check_index::Bool = true)
```

`TrainedClassifier`オブジェクトを関数として呼び出し、`index`内の文書をスコアリングすることを可能にするメソッド定義。このメソッドは`score`関数に委譲します。

スコアは、各文書が訓練された分類器（`classifier.labels`）の各ラベルにどれだけ一致しているかを反映します。

結果として得られるスコアは、各文書と各ラベルの確率の行列になります。

スコアの次元: `num_documents x num_labels`、つまり、位置[1,3]は、最初の文書が3番目のラベル/クラスに対応する確率に相当します。

各文書に対して最も良いラベルを選択するには、`argmax(scores, dims=2)`を使用できます。

# 引数

  * `index::AbstractDocumentIndex`: スコアリングされる文書を含むインデックス。
  * `return_labels::Bool`（オプション）: `true`の場合、スコアの代わりに最も確率の高いラベルを返します。デフォルトは`false`です。
  * `check_index::Bool`（オプション）: `true`の場合、インデックスIDが分類器のトレーニングで使用されたものと一致することを確認するチェックを実行します。デフォルトは`true`です。

# 戻り値

  * インデックス内の各文書に対応する[0, 1]の範囲のスコアのベクトル。

# 例

```julia
# `index`と`classifier`が事前に定義されていると仮定
scores = classifier(index)
```

各文書に対して最高スコアのラベルを選択します：

```julia
best_labels = score(index, classifier; return_labels = true)
```

このメソッドは、スコアリングのために文書インデックスに訓練された分類器モデルを適用する便利で直感的な方法を提供します。
