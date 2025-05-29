```
HydroPump <: HydroUnit
```

水力ポンプは、`HydroUnit`ノードとしてモデル化されています。

水力ポンプは、2つの[`HydroReservoir`](@ref)sの間に位置し、水をポンプで移動させることによって、1つの貯水池から別の貯水池へ水を移すことを可能にします。

## フィールド

  * **`id`** はノードの名前/識別子です。
  * **`cap::TimeProfile`** は、時間単位あたりの出力または体積で表される設置されたポンピング能力です。
  * **`pq_curve::AbstractPqCurve`** は、電力と水のポンピングの関係を説明します。
  * **`opex_var::TimeProfile`** は、生成されたエネルギー単位あたりの変動する運用コストです。
  * **`opex_fixed::TimeProfile`** は、固定運用コストです。
  * **`electricity_resource::Resource`** は、入力として取り込まれる電力資源（消費される）です。
  * **`water_resource::Resource`** は、入力として取り込まれ、出力として排出（ポンプで移動）される水資源です。
  * **`data::Vector{<:Data}`** は、追加データ（*例*、[`AbstractScheduleType`](@ref)を通じた投資や制約のため）です。フィールド`data`は、コンストラクタの使用によって条件付きです。
