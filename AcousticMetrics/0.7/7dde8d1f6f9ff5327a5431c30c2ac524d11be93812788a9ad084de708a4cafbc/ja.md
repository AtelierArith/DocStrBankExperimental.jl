```
PressureTimeHistory(sm::AbstractNarrowbandSpectrum, p=similar(halfcomplex(sm)))
```

ナローバンドスペクトル `sm` から圧力時間履歴を構築します。

オプションの `p` 引数は、圧力時間履歴の圧力ベクトルを格納するために使用され、`inputlength(sm)` の長さを持つ必要があります。
