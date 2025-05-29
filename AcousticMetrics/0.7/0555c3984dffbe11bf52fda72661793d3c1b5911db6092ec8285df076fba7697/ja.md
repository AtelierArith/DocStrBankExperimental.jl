```
MSPSpectrumAmplitude{IsEven,IsTonal,Tel} <: AbstractNarrowbandSpectrum{IsEven,IsTonal,Tel}
```

狭帯域周波数の関数としての平均二乗圧力振幅の表現。

`IsEven` パラメータは、スペクトルの長さが偶数かどうかを示す `Bool` であり、ナイキスト周波数の計算に影響を与えます。`IsTonal` `Bool` パラメータが `true` の場合、平均二乗圧力スペクトルはトーナルであり、したがって離散周波数に集中していることを示します。`false` の場合、圧力スペクトルは各周波数帯域で一定であると仮定されます。
