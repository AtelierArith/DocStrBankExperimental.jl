```julia
p3p_ransac(points, pixels, K; threshold = 1.0, ransac_kwargs...)
```

P3P Ransacアルゴリズムを使用してポーズ`K*[R|t]`を復元します。

# 引数:

  * `points`: 3Dポイント `(x, y, z)` の形式。
  * `pixels`: 画像平面への対応する投影 `(x, y)` 形式。これらの値は、**事前に**内部行列によって割り算され、正規化されます。例: `Ki = inv(K); p = Ki [x, y, 1]; p /= norm(p)`。
  * `K`: カメラの内部パラメータ。
  * `threshold::Real`: 投影点とそのターゲットピクセルとの最大距離（ピクセル単位）。この距離内であれば、その点はインライヤーと見なされます。デフォルト値は`1.0`です。
  * `ransac_kwargs...`: [`ransac`](@ref)に渡されるキーワード引数。

# 戻り値:

`Vector{SMatrix{3, 4, Float64}}` の最大4つの可能な解のベクトル。各要素は投影行列 `P = K * [R|t]` です。純粋な変換行列を得るには、`P` に `inv(K)` を掛けます。

# 参考文献:

```
リンク: https://cmp.felk.cvut.cz/~pajdla/gvg/GVG-2016-Lecture.pdf
章: 7.3 キャリブレーションされたカメラポーズ計算。
ページ: 51-59
```
