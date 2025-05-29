```julia
d4c(x, fs, timeaxis, f0; opt)

```

D4CはD4Cによって推定された非周期性を計算します。

**パラメータ**

  * `x` : 入力信号
  * `fs` : サンプリング周波数
  * `time_axis` : 時間軸
  * `f0` : F0コンター

**戻り値**

  * `aperiodicity` : D4Cによって推定された非周期性。
