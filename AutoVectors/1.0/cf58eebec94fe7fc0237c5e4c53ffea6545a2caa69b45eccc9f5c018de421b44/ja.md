```
fftav(f::AutoVector{Float64},delta)
```

均等なグリッドで間隔 delta でサンプリングされた実関数 f(x) に対して、タプル (F, freqsp, len) を返します。ここで、F は AutoVector(ComplexF64) としてのフーリエ変換、freqsp は F の周波数間隔、len は FFT に使用されるベクトルの長さです（ifftav で使用されます）。暗黙的に、関数は入力の範囲外ではゼロであると仮定されています。正規化は通常の離散 FT の慣習とは異なり、間隔を組み込んでおり、連続的な積分に対応しています。FT は次のように定義されます。

$$
F(k) = \frac{1}{\sqrt{2 \pi}} \int dx e^{-i k x} f(x)
$$
