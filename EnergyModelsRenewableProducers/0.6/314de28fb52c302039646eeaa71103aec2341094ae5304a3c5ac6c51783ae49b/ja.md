```
HydroGenerator <: HydroUnit
```

水力発電機は、`HydroUnit`ノードとしてモデル化されています。

水力発電機は、2つの[`HydroReservoir`](@ref)の間、または[`HydroReservoir`](@ref)と海に対応する`Sink`ノードの間に位置しています。これは、[`HydroGate`](@ref)とは異なり、[`AbstractPqCurve`](@ref)を通じて説明される発電を可能にします。

## フィールド

  * **`id`** はノードの名前/識別子です。
  * **`cap::TimeProfile`** は、設置された排水または発電能力です。
  * **`pq_curve::AbstractPqCurve`** は、電力と排水（水）の関係を説明します。
  * **`opex_var::TimeProfile`** は、生産されたエネルギー単位あたりの変動運用コストです。
  * **`opex_fixed::TimeProfile`** は、固定運用コストです。
  * **`electricity_resource::Resource`** は、出力として生成される電力資源です。
  * **`water_resource::Resource`** は、入力として取り込まれ、出力として排出される水資源です。
  * **`data::Vector{<:Data}`** は、追加データ（*例*、[`AbstractScheduleType`](@ref)を通じた投資や制約のため）。フィールド`data`は、コンストラクタの使用によって条件付きです。
