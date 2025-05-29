```
spectrum(input_signal, bs::Int, window = hanning(bs); fs::Int = 1, 
         overlap = 0.5)
```

信号のスペクトルの推定

**入力**

  * `input_signal::Vector{Real}`: 入力信号
  * `bs::Int`: ブロックサイズ
  * `window`: 窓関数
  * `fs::Int`: サンプリングレート
  * `overlap`: セグメント間のオーバーラップ比

**出力**

  * `y`: 信号スペクトル
  * `freq`: 周波数範囲

**利用可能な窓関数**

**DSP.jlから**

  * `rect`
  * `hann` (デフォルト)
  * `hamming`
  * `tukey`
  * `cosine`
  * `lanczos`
  * `triang`
  * `bartlett`
  * `gaussian`
  * `bartlett_hann`
  * `blackman`
  * `kaiser`
  * `dpss`

**StructuralVibration.jlから**

  * `exponential`
  * `force`
  * `flattop`
  * `nutall`
  * `blackman_nutall`
  * `blackman_harris`
  * `parzen`
  * `planck`
