```
TrainedClassifier
```

`TrainedClassifier`構造体は、訓練された分類モデルを表現し、操作するために使用されます。つまり、特定の文書に対して最も適切な`label`を選択します。

これは、特定の概念に対する関連性に基づいて文書を分析し、スコアを付けるために必要なすべての情報をカプセル化しています。

# フィールド

  * `index_id`: この概念に関連付けられた`AbstractDocumentIndex`の一意の識別子。
  * `source_doc_ids`: 概念モデルの訓練に使用された`AbstractDocumentIndex`からの文書のインデックス。提供されている場合は`index.docs`に対応します。
  * `concept`: このモデルが分析するために訓練された特定の概念（文字列として）。
  * `docs`: 概念を反映するように修正された書き換えられた文書のコレクション。
  * `embeddings`: モデルの訓練に使用される書き換えられた文書の埋め込み。列は文書、行は次元です。
  * `coeffs`: 訓練されたロジスティック回帰モデルの係数。`embeddings`の各次元にマッピングされます。

# 例

```julia
index = build_index(...)

# 概念の訓練
concept = train_concept(index, "sustainability")

# スコアリングのためのTrainedConceptの使用
scores = score(index, concept)
# またはファンクタとして使用: `scores = concept(index)`

# モデルの詳細にアクセス
println("Concept: ", concept.concept)
println("Coefficients: ", concept.coeffs)
println("Source Document IDs: ", concept.source_doc_ids)
println("Re-written Documents: ", concept.docs) # 結果が悪い場合のデバッグに便利
```
