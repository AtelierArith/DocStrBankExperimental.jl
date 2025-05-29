```
melspectrogram(s, n=div(length(s), 8), args...; fs=1, nmels::Int=128, fmin::Real=0.0f0, fmax::Real=fs / 2.0f0, window=hanning, kwargs...)
```

DOCSTRING

#引数:

  * `s`: 信号
  * `n`: 各ウィンドウのポイント数
  * `args`: `spectrogram`に送信される
  * `fs`: サンプリング周波数
  * `nmels`: メル周波数の数
  * `fmin`: 最小周波数
  * `fmax`: 最大周波数
  * `window`: ウィンドウ関数、デフォルトはhanning
  * `kwargs`: `spectrogram`に送信される
