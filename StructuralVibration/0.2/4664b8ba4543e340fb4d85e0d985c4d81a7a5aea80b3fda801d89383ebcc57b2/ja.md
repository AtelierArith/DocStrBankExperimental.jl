```
tfestimate(input_signal, output_signal, bs::Int, window_input = hanning(bs),
           window_output = window_input; fs::Int = 1, overlap = 0., type = :h1)
```

二つの信号間の片側伝達関数の推定

**入力**

  * `input_signal::Vector{Real}`: 入力信号
  * `output_signal::Vector{Real}`: 出力信号
  * `bs::Int` ブロックサイズ
  * `window_input`: 入力信号のウィンドウ関数
  * `window_output`: 出力信号のウィンドウ関数
  * `fs::Int`: サンプリングレート
  * `overlap::Real`: セグメント間のオーバーラップ比
  * `type::Symbol`: 推定する伝達関数のタイプ

      * `:h1` (デフォルト)
      * `:h2`
      * `:h3` - h3 = (h1 + h2)/2
      * `:hv` - hv = sqrt(h1*h2)

**出力**

  * `H`: 伝達関数
  * `freq`: 周波数範囲
  * `coh`: コヒーレンス

**利用可能なウィンドウ関数**

**DSP.jlから**

  * `rect`
  * `hann` (デフォルト)
  * `hamming`
  * `tukey`
  * `cosine`
  * `lanczos`
  * `triang`
  * `bartlett`
  * `bartlett_hann`
  * `gaussian`
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
