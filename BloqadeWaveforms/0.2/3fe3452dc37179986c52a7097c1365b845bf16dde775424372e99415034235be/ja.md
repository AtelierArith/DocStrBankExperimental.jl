```
piecewise_linear_interpolate(waveform;[max_vale=Inf64,max_slope=Inf64,min_step=0.0])
```

波形を受け取り、いくつかの制約に従って線形補間に変換する関数です。この関数は、区分線形波形を返します。波形が区分線形の場合、制約のみがチェックされます。

# 引数

  * `waveform`: ['Waveform'](@ref) を離散化します。

# キーワード引数

  * `min_step`: 補間に使用される最小のステップ
  * `max_slope`: 補間に使用される最大の傾き
  * `atol`: 補間の許容誤差で、これは線形補間と波形の間の面積に対する制約です。
