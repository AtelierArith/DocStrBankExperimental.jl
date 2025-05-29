```julia
p3p_ransac(points, pixels, pdn_pixels, K; threshold = 1.0, ransac_kwargs...)
```

P3P Ransacアルゴリズムを使用してポーズ`K*[R|t]`を復元します。

# 引数:

  * `points`: `(x, y, z)`形式の3Dポイント
  * `pixels`: `(x, y)`形式の画像平面への対応する投影。
  * `pdn_pixels`: `K`の内部パラメータで前処理され、正規化された画像平面への対応する投影。例: `Ki = inv(K); p = Ki [x, y, 1]; p /= norm(p)`。
  * `K`: カメラの内部パラメータ。
  * `threshold`: 投影された点とそのターゲットピクセルとの最大距離（ピクセル単位）。この距離内であれば、その点はインライヤーと見なされます。デフォルト値は`1.0`です。
  * `ransac_kwargs...`: [`ransac`](@ref)に渡されるキーワード引数。

# 戻り値:

`n_inliers, (projection, inliers, error)`。

  * `n_inliers`: `projection`のインライヤーの数。
  * `projection`: `points`を画像平面に投影する`K * P`投影行列。
  * `inliers`: どの点がインライヤーであるかを示すブールベクトル。
  * `error`: `pose`の平均再投影誤差。

# 参考文献:

```
リンク: https://cmp.felk.cvut.cz/~pajdla/gvg/GVG-2016-Lecture.pdf
章: 7.3 キャリブレーションされたカメラポーズ計算。
ページ: 51-59
```
