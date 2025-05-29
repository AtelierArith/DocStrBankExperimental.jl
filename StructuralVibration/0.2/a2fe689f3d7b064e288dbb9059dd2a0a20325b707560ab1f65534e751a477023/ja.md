```
welch(input_signal, bs::Int, window = hanning(bs); fs::Int = 1,
      overlap = 0.5, scaling = :psd)
```

ウェルチ法を使用した信号の片側オートパワー関数の推定

**入力**

  * `input_signal::Vector{Real}`: 入力信号
  * `bs::Int`: ブロックサイズ
  * `window`: 窓関数
  * `fs::Int`: サンプリングレート
  * `overlap`: セグメント間のオーバーラップ比
  * `scaling`: PSDのスケール - 詳細については https://community.sw.siemens.com/s/article/the-autopower-function-demystified を参照してください

      * `:psd` (デフォルト) - パワースペクトル密度
      * `:esd` - オートパワーエネルギースペクトル密度
      * `:spectrum` - オートパワースペクトル
      * `:linear` - オートパワー線形

**出力**

  * `pxx`: オートパワー
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

**注意** welch関数はすでに`DSP.jl`に`welch_pgram`という名前で実装されています。関数`welch`は教育的目的のためにここに実装されています。
