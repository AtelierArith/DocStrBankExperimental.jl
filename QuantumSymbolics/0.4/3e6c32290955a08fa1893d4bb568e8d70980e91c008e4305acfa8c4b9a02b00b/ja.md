安定器タブローによって定義された状態

完全な機能を得るためには、`QuantumClifford`ライブラリもインポートする必要があります。

```jldoctest
julia> using QuantumClifford, QuantumOptics # 安定器タブローの内部表現とケトへの変換に必要

julia> StabilizerState(S"XX ZZ")
𝒮₂

julia> express(StabilizerState(S"-X"))
Ket(dim=2)
  basis: Spin(1/2)
  0.7071067811865475 + 0.0im
 -0.7071067811865475 + 0.0im
```
