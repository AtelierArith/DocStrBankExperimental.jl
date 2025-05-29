```
score(index::AbstractDocumentIndex,
    classifier::TrainedClassifier;
    check_index::Bool = true)
```

提供された `index` 内のすべての文書を `TrainedClassifier` に基づいてスコアリングします。

スコアは、各文書がトレーニングされた分類器 (`classifier.labels`) の各ラベルにどれだけ一致しているかを反映します。

結果として得られるスコアは、各文書と各ラベルの確率の行列になります。

スコアの次元: `num_documents x num_labels`、つまり、位置 [1,3] は最初の文書が3番目のラベル/クラスに対応する確率に相当します。

各文書に対して最良のラベルを選択するには、`argmax(scores, dims=2)` を使用できます。

# 引数

  * `index::AbstractDocumentIndex`: スコアリングされる文書を含むインデックス。
  * `classifier::TrainedClassifier`: スコアリングに使用されるトレーニング済みの分類器モデル。
  * `return_labels::Bool` (オプション): `true` の場合、スコアの代わりに最も確率の高いラベルを返します。デフォルトは `false` です。
  * `check_index::Bool` (オプション): `true` の場合、提供されたインデックスと分類器のトレーニングに使用されたインデックスのIDが一致するかをチェックします。デフォルトは `true` です。

# 戻り値

  * スコアの行列。各行はインデックス内の文書に対応し、各列はそのラベルの確率に対応します。

# 例

```julia
# `index` と `classifier` が事前に定義されていると仮定
scores = score(index, classifier)
```

各文書に対して最高のスコアのラベルを選択します：

```julia
scores = score(index, classifier)
label_ids = argmax(scores, dims = 2) |> vec |> x -> map(i -> i[2], x)
best_labels = classifier.labels[label_ids]
```

または、単に `return_labels=true` を指定して最良のラベルを直接取得することもできます：

```julia
score(index, classifier; return_labels = true)
```
