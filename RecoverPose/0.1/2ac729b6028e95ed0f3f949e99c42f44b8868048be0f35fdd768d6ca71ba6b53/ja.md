```julia
p3p(points, pdn_pixels::AbstractVector{SVector{3, T}}, K)
```

P3Pアルゴリズムを使用してポーズを復元します。

# 引数:

  * `points: (x, y, z)`形式の3Dポイントのベクトル。
  * `pdn_pixels::AbstractVector{SVector{3, Float64}}`:   `K`の内部パラメータで前処理され、正規化された`points`の画像平面への対応する投影。   例: `Ki = inv(K); p = Ki [x, y, 1]; p /= norm(p)`。
  * `K::SMatrix{3, 3, Float64}`: カメラの内部パラメータ。

# 戻り値:

`Vector{SMatrix{3, 4, Float64}}` 最大4つの可能な解のベクトル。各要素は投影行列`P = K * [R|t]`です。純粋な変換行列を取得するには、`P`を`inv(K)`で掛けます。

# 参考文献:

```
リンク: https://cmp.felk.cvut.cz/~pajdla/gvg/GVG-2016-Lecture.pdf
章: 7.3 キャリブレーションされたカメラポーズ計算。
ページ: 51-59
```
