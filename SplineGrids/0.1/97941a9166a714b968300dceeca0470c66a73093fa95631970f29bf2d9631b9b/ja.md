```
SplineGrid(
    spline_dimensions,
    control_points,
    weights,
    eval)
```

SplineGridは、定義されたグリッド上で定義されたスプラインを評価するためのすべての情報を含む`SplineGrids.jl`パッケージの中心的なオブジェクトです。

## フィールド

  * `spline_dimensions`: スプラインの次元ごとのSplineDimensionで、基底関数を評価するためのデータを含みます。
  * `control points`: スプラインの形状を定義し、どの次元に埋め込まれているかを示す点です。
  * `weights`: NURBSを定義するための制御点の重みです。
  * `eval`: 評価されたスプライングリッドが格納される配列です。
