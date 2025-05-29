```
IntensityCamera(met::Kerr{T}, θo, αmin, αmax, βmin, βmax, res::Int; A=Matrix) where {T}
```

強度カメラのコンストラクタ。

# 引数

  * `met::Kerr{T}`: ケル metric。
  * `θo`: 観測者の傾斜角。θo ∈ (0, π)。
  * `αmin`: αの最小値。
  * `αmax`: αの最大値。
  * `βmin`: βの最小値。
  * `βmax`: βの最大値。
  * `res::Int`: スクリーンの解像度。
  * `A=Matrix`: 使用する行列のタイプを指定するオプション引数。GPU計算にはGPUMatrixを使用できます。

# 戻り値

  * `IntensityCamera{T, A}`: 強度カメラオブジェクト。
