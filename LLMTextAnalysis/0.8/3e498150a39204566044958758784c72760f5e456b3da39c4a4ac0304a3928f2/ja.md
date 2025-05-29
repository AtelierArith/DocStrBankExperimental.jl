```
TrainedSpectrum
```

`TrainedSpectrum`は、2つの対照的な概念によって定義されたスペクトルに沿って文書をスコアリングするために使用されます。

これは、指定されたスペクトルとの整合性に基づいて文書を評価しスコアリングするために必要な基本情報をカプセル化しています。

注意: `TrainedSpectrum`はファンクタの動作をサポートしており、スペクトルとの整合性に基づいて`AbstractDocumentIndex`内の文書をスコアリングするための関数として使用できます。

# フィールド

  * `index_id`: スペクトルに関連付けられた`AbstractDocumentIndex`の一意の識別子。
  * `source_doc_ids`: スペクトルモデルのトレーニングに使用された`AbstractDocumentIndex`からの文書のインデックス。`index.docs`に対応します。
  * `spectrum`: スペクトルを定義する2つの対照的な概念（文字列として）のタプル。
  * `docs`: スペクトルの両端に整合するように修正された書き換えられた文書のコレクション。
  * `embeddings`: モデルのトレーニングに使用される書き換えられた文書の埋め込み。列は文書、行は次元です。
  * `coeffs`: `embeddings`内の各次元に対応するトレーニングされたロジスティック回帰モデルの係数。

# 例

```julia

index = build_index(...)

# スペクトルモデルを作成してトレーニングする
spectrum = TrainedSpectrum(index, ("innovation", "tradition"))

# スコアリングのためのTrainedSpectrumの使用
scores = score(index, concept)
# またはファンクタとして使用: `scores = spectrum(index)`

# モデルの詳細にアクセス
println("Spectrum: ", spectrum.spectrum)
println("Coefficients: ", spectrum.coeffs)
println("Source Document IDs: ", spectrum.source_doc_ids)
println("Re-written Documents: ", spectrum.docs) # 結果が悪い場合のデバッグに良い
```
