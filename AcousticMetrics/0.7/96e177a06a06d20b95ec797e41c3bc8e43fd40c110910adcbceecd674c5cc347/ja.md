```
PressureSpectrumPhase{IsEven,IsTonal,Tel} <: AbstractNarrowbandSpectrum{IsEven,IsTonal,Tel}
```

狭帯域周波数の関数としての音響圧相の表現。

`IsEven` パラメータは、スペクトルの長さが偶数かどうかを示す `Bool` であり、ナイキスト周波数の計算に影響を与えます。`IsTonal` `Bool` パラメータが `true` の場合、位相スペクトルはトーナルであり、したがって離散周波数に集中しています。`false` の場合、スペクトルは各周波数帯域で一定であると見なされます。
