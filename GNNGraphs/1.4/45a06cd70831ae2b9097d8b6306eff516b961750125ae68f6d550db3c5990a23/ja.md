```
scaled_laplacian(g, T=Float32; dir=:out)
```

グラフ `g` のスケーリングラプラシアン行列は、$\hat{L} = \frac{2}{\lambda_{max}} L - I$ と定義され、ここで $L$ は正規化ラプラシアン行列です。

# 引数

  * `g`: `GNNGraph`。
  * `T`: 結果の要素型。
  * `dir`: 考慮されるエッジの方向性 (:out, :in, :both)。
