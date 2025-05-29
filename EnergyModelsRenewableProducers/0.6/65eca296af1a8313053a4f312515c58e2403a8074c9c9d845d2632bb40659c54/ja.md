```
HydroGate <: EMB.NetworkNode
```

水門は、`NetworkNode`ノードとしてモデル化されています。

これは、発電なしで個々の貯水池間の水流の出口/入口および最小/最大要件をモデル化するために使用できます。

## フィールド

  * **`id`** はノードの名前/識別子です。
  * **`cap::TimeProfile`** は設置された排水能力です。
  * **`opex_var::TimeProfile`** はゲートを通る水流に対する変動運用コストです。
  * **`opex_fixed::TimeProfile`** は固定運用コストです。
  * **`resource::ResourceCarrier`** は水資源の種類であり、ゲートは水を排出するためにのみ使用されます。
  * **`data::Vector{<:Data}`** は追加データ（*例*、[`AbstractScheduleType`](@ref)を通じた投資や制約のため）。フィールド`data`はコンストラクタの使用によって条件付きです。
