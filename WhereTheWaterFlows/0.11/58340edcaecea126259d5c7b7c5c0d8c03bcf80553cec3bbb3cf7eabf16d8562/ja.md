```
catchment(dir, ij)
```

1つまたは複数のグリッドポイント ij の集水域を計算します。必要に応じて、`make_boundaries([c], [1])`を使用して集水域の境界を計算できます。

入力

  * dir – 方向フィールド
  * ij – ポイントのインデックス（2タプルまたはCartesianIndex）または複数のためのVector{CartesianIndex}

返り値

  * catchment – BitArray

ヒント: 1つのグリッドポイントだけずれていると、小さな集水域と巨大な集水域の違いが生じることがあります！

関連情報: `catchments`
