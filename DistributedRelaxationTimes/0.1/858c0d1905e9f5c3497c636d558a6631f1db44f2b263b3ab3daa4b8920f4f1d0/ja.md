```
compute_DRT(frequencies, measurements; <keyword arguments>)
```

リラクゼーション時間の分布をRBF離散化とティホノフ正則化を使用して計算します。

基本的な入力は、一連の周波数と、それらの周波数で行われたインピーダンス測定値です。計算を微調整するためのいくつかのキーワード引数もあります。

## キーワード引数

  * `method::String="im"`: DRTを計算するために使用される測定値の部分。
  * `rbf_kernel = SqExponentialKernel()`: DRTを離散化するために使用されるRBF。
  * `width_coeff::Float64=0.10`: RBFの形状係数に影響を与えるハイパーパラメータ。
  * `λ::Float64=1e-2`: 正則化の度合いを調整するハイパーパラメータ。
  * `peak_strictness::Float64=0.01`: 最高のピークのパーセンテージ未満の振幅を持つピークを除去することによってDRTのアーティファクトを避けるための尺度。

```
