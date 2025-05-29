```
EnergyScale
```

EnergyScaleは、X線データに関連するエネルギー軸を表現する方法です。このスケールは、EDS検出器で発生するさまざまな非線形性を処理するために線形、ポリノミアル、または???である可能性があり、WDS波形スキャンも処理できます。

実装:

```
channel(::Type{Float64}, eV::AbstractFloat, sc::EnergyScale)::Float64
energy(ch::Int, sc::EnergyScale)::Float64
```
