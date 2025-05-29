```julia
essential_ransac(pd1, pd2, focal_sum; threshold = 1.0, ransac_kwargs...)
```

RANASCスキームを使用してエッセンシャル行列を計算します。

# 引数:

  * `pd1`:   最初の画像における一致した点の `(x, y)` 形式のピクセル座標 **をK^-1で前割り** したもの。
  * `pd2`:   2番目の画像における一致した点の `(x, y)` 形式のピクセル座標 **をK^-1で前割り** したもの。
  * `focal_sum`: `fx + fy`。
  * `threshold`: エピポーラ制約の最大誤差。デフォルトは `1.0`。
  * `ransac_kwargs...`: [`ransac`](@ref) に渡されるキーワード引数。

# 戻り値:

`n_inliers, (E, inliers, repr_error)`:

  * インライヤーの数
  * タプル: エッセンシャル行列、インライヤーのブールベクトル、誤差値。
