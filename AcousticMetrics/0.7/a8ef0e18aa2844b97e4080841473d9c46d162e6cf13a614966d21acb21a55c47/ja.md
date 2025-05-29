```
PowerSpectralDensityAmplitude{IsEven,Tel} <: AbstractNarrowbandSpectrum{IsEven,false,Tel}
```

狭帯域周波数の関数としての音響パワースペクトル密度振幅の表現。

`IsEven` パラメータは、スペクトルの長さが偶数かどうかを示す `Bool` であり、ナイキスト周波数の計算に影響を与えます。パワースペクトル密度はトーンに対しては明確に定義されないため、`IsTonal` パラメータは常に `false` です。
