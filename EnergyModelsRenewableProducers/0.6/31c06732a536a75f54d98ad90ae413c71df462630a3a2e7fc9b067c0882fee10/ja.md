```
HydroReservoir{T} <: EMB.Storage{T}
```

調整された水力発電用の貯水池で、`Storage`ノードとしてモデル化されています。

`HydroReservoir`は、[`HydroStor`](@ref)や[`PumpedHydroStor`](@ref)ノードとは異なり、潜在エネルギーを通じて水の形で蓄えられたエネルギーをモデル化しています。これは、[`HydroGenerator`](@ref)ノードと一緒にのみ使用できます。

## フィールド

  * **`id`** はノードの名前/識別子です。
  * **`vol::EMB.UnionCapacity`** は`HydroReservoir`ノードの貯蔵容量パラメータです（通常は百万立方メートル）。
  * **`vol_inflow::TimeProfile`** は貯水池への水の流入量です（通常は時間単位あたり百万立方メートル）。
  * **`stor_res::ResourceCarrier`** は蓄えられた`Resource`です。
  * **`data::Vector{<:Data}`** は追加データです（*例*、投資や[`AbstractScheduleType`](@ref)を通じた制約のため）。フィールド`data`はコンストラクタの使用によって条件付きです。
