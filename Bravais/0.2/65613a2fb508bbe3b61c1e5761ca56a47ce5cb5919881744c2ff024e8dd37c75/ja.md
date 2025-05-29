```
Bravais.ReciprocalPoint{D} <: AbstractPoint{D}
```

`D`次元逆空間における単一の点を定義する、`SVector{D, Float64}`のラッパー型です。

Bravais.ReciprocalPointの座標は、一般的に関連するBravais.ReciprocalBasisに対して指定されていると仮定されます。直交座標に変換するには、[`cartesianize`](@ref)を参照してください。
