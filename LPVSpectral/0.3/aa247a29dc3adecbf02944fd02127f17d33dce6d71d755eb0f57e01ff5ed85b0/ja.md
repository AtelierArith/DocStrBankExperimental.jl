```
mfcc(s, args...; nmfcc::Int=20, nmels::Int=128, window=hanning, kwargs...)
```

メル周波数ケプストラム係数 (MFCC) を計算します。[Mel-frequency cepstral coefficients (MFCCs)](https://en.wikipedia.org/wiki/Mel-frequency_cepstrum)

# 引数:

  * `s`: 信号
  * `args`: `spectrogram` に送信される
  * `nmfcc`: 係数の数
  * `nmels`: メル周波数の数
  * `window`: 窓関数、デフォルトは hanning
  * `kwargs`: `spectrogram` に送信される
