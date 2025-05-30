```
SimpleHydrogenStorage{T} <: AbstractH2Storage{T}
```

`Storage`ノードでは、最大放電使用量が充電容量に直接リンクされており、充電容量よりも大きな放電使用量を持つことはできず、乗数`discharge_charge`があります。

# フィールド

  * **`id`** はノードの名前/識別子です。
  * **`charge::EMB.UnionCapacity`** は`SimpleHydrogenStorage`ノードの充電パラメータです。選択したタイプに応じて、充電パラメータには変動OPEX、固定OPEX、および/または容量が含まれる場合があります。
  * **`level::EMB.UnionCapacity`** は`SimpleHydrogenStorage`ノードのレベルパラメータです。選択したタイプに応じて、充電パラメータには変動OPEXおよび/または固定OPEXが含まれる場合があります。
  * **`stor_res::Resource`** は保存された[`Resource`](@extref EnergyModelsBase.Resource)です。
  * **`input::Dict{<:Resource, <:Real}`** は変換値`Real`を持つ入力[`Resource`](@extref EnergyModelsBase.Resource)です。
  * **`output::Dict{<:Resource, <:Real}`** は変換値`Real`を持つ生成された[`Resource`](@extref EnergyModelsBase.Resource)です。これはリンクに関連するものであり、保存された[`Resource`](@extref EnergyModelsBase.Resource)として、出力値は計算に利用されません。
  * **`data::Vector{<:Data}`** は追加データ（*例*、投資用）です。フィールド`data`はコンストラクタの使用によって条件付きです。
  * **`discharge_charge::Float64`** は充電率に対する最大放電率を指定するための乗数です。`2.0`の値は、設置された充電容量に対して放電率が2倍になることを意味します。
  * **`level_charge::Float64`** は設置されたストレージレベル容量に対する設置されたストレージ充電容量を指定するための乗数です。これは、一般的なモデルの場合の入力データのチェックや、[`AbstractInvestmentModel`](@extref EnergyModelsBase.AbstractInvestmentModel)の場合の投資制限に使用されます。
