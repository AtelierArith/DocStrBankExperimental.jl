```
abstract type Policy <: Modification
```

これは、モデル化されるポリシーを表すModificationのサブタイプです。

基本ポリシータイプは、E4STで標準ポリシーを定義する際に使用されます。これらは、`type`フィールドを持つconfigファイルのmodsとして指定されます。

現在、基本ポリシータイプは6種類あります。必要に応じて新しいポリシータイプも追加できます。

## ポリシー (Policyサブタイプ)

  * [`ITC`](@ref)
  * [`PTC`](@ref)
  * [`EmissionCap`](@ref)
  * [`EmissionPrice`](@ref)
  * [`RPS`](@ref)
  * [`CES`](@ref)
