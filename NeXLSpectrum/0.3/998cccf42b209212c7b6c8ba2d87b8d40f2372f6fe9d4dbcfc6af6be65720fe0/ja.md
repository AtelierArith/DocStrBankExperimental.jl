```
channel(::Type{Float64}, eV::AbstractFloat, sc::EnergyScale)::Float64
```

指定されたエネルギーX線（eV単位）の分数チャネルインデックスを返します。

```
channel(eV::AbstractFloat, sc::EnergyScale)::Int
channel(eV::Float64, spec::Spectrum)::Int
channel(eV::Float64, det::EDSDetector)::Int
```

指定されたエネルギーX線（eV単位）のチャネルの整数インデックスを返します。
