```
PressureSpectrumAmplitude(pth::AbstractPressureTimeHistory, istonal::Bool=false, hc=similar(pressure(pth)))
```

圧力時間履歴から圧力振幅の狭帯域スペクトルを構築します。

オプション引数 `hc` は圧力時間履歴の離散フーリエ変換を格納するために使用され、`inputlength(pth)` の長さを持つ必要があります。`istonal` の `Bool` 引数が `true` の場合、圧力スペクトルはトーナルであり、したがって離散周波数に集中していることを示します。`false` の場合、スペクトルは各周波数帯域で一定であると仮定されます。
