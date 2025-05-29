```
HydroStor{T} <: HydroStorage{T}
```

調整された水力発電ストレージで、`Storage`ノードとしてモデル化されています。調整された水力ストレージノードは、`discharge`のための容量を必要とし、モデルからの必要な流入はありませんが、モデルの外部からの水の流入は必要です。ただし、`input`フィールドが必要です。

## フィールド

  * **`id`** はノードの名前/識別子です。
  * **`level::EMB.UnionCapacity`** は`HydroStor`ノードのレベルパラメータです。選択されたタイプに応じて、充電パラメータには可変OPEXおよび/または固定OPEXが含まれる場合があります。
  * **`discharge::EMB.UnionCapacity`** は`HydroStor`ノードの放出パラメータです。選択されたタイプに応じて、放出パラメータには可変OPEX、固定OPEX、および/または容量が含まれる場合があります。
  * **`level_init::TimeProfile`** はダムにおける初期蓄積エネルギーです。
  * **`level_inflow::TimeProfile`** は運用期間ごとの電力の流入です。
  * **`level_min::TimeProfile`** は`HydroStorage`ノードに残さなければならない貯水池容量の最小割合です。
  * **`stor_res::ResourceCarrier`** は蓄積された`Resource`です。
  * **`input::Dict{Resource, Real}`** は入力`Resource`です。`HydroStor`の場合、このフィールドは省略できます。
  * **`output::Dict{Resource, Real}`** は蓄積されたリソースのみを含むことができます。
  * **`data::Vector{Data}`** 追加データ（*例*、投資用）。フィールド`data`はコンストラクタの使用によって条件付きです。
