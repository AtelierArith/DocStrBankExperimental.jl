```
SlowLightIntensityCamera(met::Kerr{T}, θo, αmin, αmax, βmin, βmax, res; A=Matrix) where {T}
```

`SlowLightIntensityCamera`オブジェクトを構築します。

# 引数

  * `met::Kerr{T}`: ケル metric。
  * `θo`: 観測者の傾斜角。θo ∈ (0, π)。
  * `αmin`: スクリーン上の最小α座標。
  * `αmax`: スクリーン上の最大α座標。
  * `βmin`: スクリーン上の最小β座標。
  * `βmax`: スクリーン上の最大β座標。
  * `res`: スクリーンの解像度（1次元あたりのピクセル数）。
  * `A`: スクリーンのピクセル情報を格納するデータ型（デフォルトは`Matrix`）。GPU計算にはGPUMatrixを使用できます。

# 戻り値

  * `SlowLightIntensityCamera`オブジェクト。
