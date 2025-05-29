```
PumpedHydroStor{T} <: HydroStorage{T}
```

ポンプ水力貯蔵は、`Storage`ノードとしてモデル化されています。ポンプ水力貯蔵ノードは、貯水池に水をポンプで送ることによってエネルギーを蓄えることを可能にします。現在の実装は、下部貯水池を必要としない簡略化されたノードです。代わりに、貯水池は無限のサイズを持つと仮定されています。

ポンプ水力貯蔵ノードは、ポテンシャルエネルギーの形でエネルギーを蓄える可能性を考慮するために、`charge`と`discharge`の両方の容量を必要とします。

## フィールド

  * **`id`** はノードの名前/識別子です。
  * **`charge::EMB.UnionCapacity`** は`PumpedHydroStor`ノードの充電パラメータです。選択されたタイプに応じて、充電パラメータには可変OPEX、固定OPEX、および/または容量が含まれる場合があります。
  * **`level::EMB.UnionCapacity`** は`PumpedHydroStor`ノードのレベルパラメータです。選択されたタイプに応じて、充電パラメータには可変OPEXおよび/または固定OPEXが含まれる場合があります。
  * **`discharge::EMB.UnionCapacity`** は`PumpedHydroStor`ノードの放電パラメータです。選択されたタイプに応じて、放電パラメータには可変OPEX、固定OPEX、および/または容量が含まれる場合があります。
  * **`level_init::TimeProfile`** はダムにおける初期蓄積エネルギーです。
  * **`level_inflow::TimeProfile`** は運用期間ごとの電力の流入です。
  * **`level_min::TimeProfile`** は`HydroStorage`ノードに残さなければならない貯水池容量の最小割合です。
  * **`stor_res::ResourceCarrier`** は蓄積された`Resource`です。
  * **`input::Dict{Resource, Real}`** は入力`Resource`です。
  * **`output::Dict{Resource, Real}`** は蓄積されたリソースのみを含むことができる一つのエントリです。
  * **`data::Vector{Data}`** 追加データ（*例*、投資用）。フィールド`data`はコンストラクタの使用によって条件付きです。
