```julia
stonemask(x, fs, timeaxis, f0)

```

StoneMaskはDioによって推定されたF0を洗練させます。

**パラメータ**

  * `x` : 入力信号
  * `fs` : サンプリング周波数
  * `time_axis` : 時間情報
  * `f0` : f0コンター

**戻り値**

  * `refined_f0` : 洗練されたF0
