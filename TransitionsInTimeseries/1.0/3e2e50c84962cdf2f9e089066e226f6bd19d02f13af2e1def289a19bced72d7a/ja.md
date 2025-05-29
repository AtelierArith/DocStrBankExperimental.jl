```
PrecomputedLowfreqPowerSpectrum
```

低周波パワースペクトル（LFPS）の繰り返し計算を効率的に行うためのすべての事前計算されたフィールドを含む構造体で、これは `0` と `1` の間の数値で、`x` のパワー密度スペクトルの低周波数に含まれるパワーの量を特徴付けます。`lfps::PrecomputedLowfreqPowerSpectrum` が初期化されると、次のようにして `x::AbstractVector` の LFPS を取得するための関数として使用できます：

```julia
lfps(x)
```
