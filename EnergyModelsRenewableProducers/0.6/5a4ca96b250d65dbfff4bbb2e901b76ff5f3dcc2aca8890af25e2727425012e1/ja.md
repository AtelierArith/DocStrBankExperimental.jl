```
ReserveBattery{T} <: AbstractBattery{T}
```

リザーブバッテリー貯蔵は、`Storage`ノードとしてモデル化されています。バッテリー貯蔵ノードは、上向きおよび下向きのリザーブの導入を許可することで、[`Battery`](@ref)ノードとは異なります。

!!! warning "実装の詳細"
      * 放電および充電能力は互いに独立しています。
      * 充電および放電効率の値は1未満でなければなりません。
      * 上向きおよび下向きのリザーブは、バッテリーから出て行くリソースとして実装されています。したがって、システムに必要な総リザーブを決定する潜在的なシンクを提供することも重要です。


## フィールド

  * **`id`** はノードの名前/識別子です。
  * **`charge::EMB.UnionCapacity`** は`BatteryStorage`ノードの充電パラメータです。選択したタイプに応じて、充電パラメータには変動OPEX、固定OPEX、および/または容量が含まれる場合があります。
  * **`level::EMB.UnionCapacity`** は`BatteryStorage`ノードのレベルパラメータです。選択したタイプに応じて、充電パラメータには変動OPEXおよび/または固定OPEXが含まれる場合があります。
  * **`discharge::EMB.UnionCapacity`** は`BatteryStorage`ノードの放電パラメータです。選択したタイプに応じて、放電パラメータには変動OPEX、固定OPEX、および/または容量が含まれる場合があります。
  * **`stor_res::ResourceCarrier`** は保存された`Resource`です。
  * **`input::Dict{Resource, Real}`** は対応する効率値を持つ入力`Resource`です。
  * **`output::Dict{Resource, Real}`** は対応する効率値を持つ出力`Resource`です。
  * **`battery_life::AbstractBatteryLife`** はバッテリーの最大寿命と対応する劣化を計算するために使用されます。
  * **`reserve_up::Vector{ResourceCarrier}`** はシステムにエネルギーを提供するために使用される`Resource`です。
  * **`reserve_down::Vector{ResourceCarrier}`** はシステムからエネルギーを取り除くために使用される`Resource`です。
  * **`data::Vector{Data}`** 追加データ（*例*、投資用）。フィールド`data`はコンストラクタの使用によって条件付きです。
