```
model_spectrum(f, h, args...; kwargs...)
```

# 引数:

  * `f`: モデル推定関数、例: `ar,arma`
  * `h`: サンプル時間
  * `args`: `f`への引数
  * `kwargs`: `f`へのキーワード引数

# 例:

```
using ControlSystemIdentification, DSP
T = 1000
s = sin.((1:T) .* 2pi/10)
S1 = spectrogram(s,window=hanning)
estimator = model_spectrum(ar,1,2)
S2 = spectrogram(s,estimator,window=rect)
plot(plot(S1),plot(S2)) # パッケージ LPVSpectral.jl が必要です
```
