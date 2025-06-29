```
gauge_fixing(AL1, AL2)
```

2つの左標準MPSテンソル間の最適なゲージ変換を、転送行列を対角化することによって計算します。単位変換と収束指標を返します。

# 引数

  * `AL1`: 参照左標準MPSテンソル
  * `AL2`: ゲージ固定されるターゲットMPSテンソル（AL1のゲージに合わせて変換されます）

# 返り値

  * `U::AbstractTensorMap`: $AL1 ≈ U * AL2 * U'$ を満たす単位変換行列
  * `conv_meas::Real`: AL1とAL2が単位変換に関して同等である場合、これは0であるべきです。これはAL1とAL2によって表されるMPSの偏差の指標です。
