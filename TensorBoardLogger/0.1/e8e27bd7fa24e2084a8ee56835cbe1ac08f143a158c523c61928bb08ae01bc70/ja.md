```
log_embeddings(logger::TBLogger, name::AbstractString, mat::AbstractMatrix; metadata, metadata_header, img_labels, step=step(logger))
```

埋め込みデータをテンソルボードにログし、PCA、t-SNE、またはUMAPを使用して3-Dまたは2-Dで視覚化します。

  * mat: サンプルを行、特徴を列として表す2-D `Matrix` のデータ
  * metadata: 各サンプルのラベルの配列。1次元目の各要素は `string` に変換されます
  * metadata_header: 1-D 配列。サンプルに複数のラベルがある場合に便利です。サイズは `metadata` の各行のサイズと同じである必要があります
  * img_labels: 各サンプルの画像ラベルを表すTBImagesオブジェクト。

      * 画像の数 (N) は `mat` のサンプル数と等しくなければなりません
      * 各画像は正方形でなければなりません (H == W)
      * 値 √N * W はテンソルボードの制限により8192以下でなければなりません。
