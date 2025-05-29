```julia
p3p_select_model(models, points, pixels; threshold = 1.0)
```

最適なポーズを`models`から選択します。

# 引数:

  * `models`: 最適なものを選択するための投影行列。
  * `points`: `(x, y, z)`形式の3Dポイント。
  * `pixels`: `(x, y)`形式の画像平面への対応する投影。
  * `threshold`: 投影されたポイントとそのターゲットピクセルの間の最大距離（ピクセル単位）。この距離内であれば、そのポイントはインライヤーと見なされます。デフォルト値は`1.0`です。

# 戻り値:

`n_inliers, (projection, inliers, error)`。

  * `n_inliers`: `projection`のインライヤーの数。
  * `projection`: `points`を画像平面に投影する`K * P`投影行列。
  * `inliers`: どのポイントがインライヤーであるかを示すブールベクトル。
  * `error`: `pose`の平均再投影誤差。
