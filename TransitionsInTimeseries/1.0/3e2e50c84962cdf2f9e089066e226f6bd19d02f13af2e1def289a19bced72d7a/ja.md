```
PrecomputedLowfreqPowerSpectrum
```

低周波パワースペクトル（LFPS）の繰り返し計算を効率的に行うために、すべての事前計算されたフィールドを含む構造体です。LFPSは、`x`のパワー密度スペクトルの低周波数に含まれるパワーの量を特徴付ける`0`と`1`の間の数値です。`lfps::PrecomputedLowfreqPowerSpectrum`が初期化されると、次のようにして`x::AbstractVector`のLFPSを取得するための関数として使用できます。

```julia
lfps(x)
```
