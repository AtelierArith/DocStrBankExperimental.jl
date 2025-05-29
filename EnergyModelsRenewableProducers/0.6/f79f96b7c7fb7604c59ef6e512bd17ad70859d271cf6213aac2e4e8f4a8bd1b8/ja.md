```
Battery{T} <: AbstractBattery{T}
```

バッテリー貯蔵は、`Storage`ノードとしてモデル化されています。バッテリー貯蔵ノードは、[`RefStorage`](@extref EnergyModelsBase.RefStorage)ノードと以下の点で異なります：

1. 放電容量を組み込むこと、
2. 充電および放電効率を含むこと、そして
3. バッテリーの劣化と寿命の短縮を導入することを許可します。

!!! warning "実装の詳細"
      * 放電容量と充電容量は互いに独立しています。
      * 充電および放電効率の値は1未満でなければなりません。


## フィールド

  * **`id`** はノードの名前/識別子です。
  * **`charge::EMB.UnionCapacity`** は`BatteryStorage`ノードの充電パラメータです。選択したタイプに応じて、充電パラメータには変動OPEX、固定OPEX、および/または容量が含まれる場合があります。
  * **`level::EMB.UnionCapacity`** は`BatteryStorage`ノードのレベルパラメータです。選択したタイプに応じて、充電パラメータには変動OPEXおよび/または固定OPEXが含まれる場合があります。
  * **`discharge::EMB.UnionCapacity`** は`BatteryStorage`ノードの放電パラメータです。選択したタイプに応じて、放電パラメータには変動OPEX、固定OPEX、および/または容量が含まれる場合があります。
  * **`stor_res::ResourceCarrier`** は保存された`Resource`です。
  * **`input::Dict{Resource, Real}`** は対応する効率値を持つ入力`Resource`です。
  * **`output::Dict{Resource, Real}`** は対応する効率値を持つ出力`Resource`です。
  * **`battery_life::AbstractBatteryLife`** はバッテリーの最大寿命と対応する劣化を計算するために使用されます。
  * **`data::Vector{Data}`** 追加データ（*例*、投資用）。フィールド`data`はコンストラクタの使用によって条件付きです。
