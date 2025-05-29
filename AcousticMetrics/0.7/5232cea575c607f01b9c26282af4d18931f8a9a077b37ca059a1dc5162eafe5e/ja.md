```
PowerSpectralDensityAmplitude(pth::AbstractPressureTimeHistory, hc=similar(pressure(pth)))
```

圧力時間履歴からのパワースペクトル密度振幅の狭帯域スペクトルを構築します。

オプションの引数 `hc` は、圧力時間履歴の離散フーリエ変換を格納するために使用され、`inputlength(pth)` の長さを持つ必要があります。
