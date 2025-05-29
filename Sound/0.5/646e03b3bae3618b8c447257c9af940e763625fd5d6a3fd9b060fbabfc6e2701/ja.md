```
phase_vocoder(x, sr = framerate(x); kwargs...)
```

信号 `x` の時間スケーリングのためのフェーズボコーダーで、サンプリングレート `sr` は Hz です。時間伸縮は `hopin` と `hopout` 変数の比率によって決まります。例えば、`hopin=242` と `hopout=161.3333`（整数は必要ありません）は、テンポを `hopin/hopout = 1.5` 増加させます。比較的同じ量を遅くするには、`hopin = 161.3333`、`hopout = 242` を選択します。

# オプション

  * `time::Real = length(x) * sr` : 処理する総時間（秒単位）
  * `hopin::Real = 121` : 入力のホップ長
  * `hopout::Real = 2*hopin` : 出力のホップ長
  * `all2pi::Any = 2π*(0:100)` : 2πの倍数（PVスタイルの周波数検索で使用）
  * `max_peak::Int = 50` : ピーク検出のためのパラメータ：ピークの数
  * `eps_peak::Real = 0.005` : ピークの最小高さ
  * `nfft::Int = 2^12` : FFTの長さ
  * `win::AbstractVector{<:Real} = hann(nfft)` : 窓関数
  * `T::DataType = Float32` : データ型
