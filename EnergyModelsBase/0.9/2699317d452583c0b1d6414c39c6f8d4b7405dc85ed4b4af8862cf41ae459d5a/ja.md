```
struct RefStorage{T} <: Storage{T}
```

参照 [`Storage`](@ref) ノード。

このノードは、[`ResourceCarrier`](@ref) または [`ResourceEmit`](@ref) のいずれかを格納するように設計されています。異なる循環的な動作を区別するために、型パラメータ `T` を通じてパラメトリック型として設計されています。パラメータ `T` はディスパッチにのみ使用され、他の情報は持たないことに注意してください。したがって、異なる [`StorageBehavior`](@ref) への切り替えは簡単です。

現在実装されている循環的な動作は、[`CyclicRepresentative`](@ref)、[`CyclicStrategic`](@ref)、および [`AccumulatingEmissions`](@ref) です。

# フィールド

  * **`id`** はノードの名前/識別子です。
  * **`charge::AbstractStorageParameters`** は、[`Storage`](@ref) ノードの充電パラメータです。選択されたタイプに応じて、充電パラメータには可変OPEX、固定OPEX、および/または容量が含まれる場合があります。
  * **`level::AbstractStorageParameters`** は、[`Storage`](@ref) ノードのレベルパラメータです。選択されたタイプに応じて、充電パラメータには可変OPEXおよび/または固定OPEXが含まれる場合があります。
  * **`stor_res::Resource`** は格納された [`Resource`](@ref) です。
  * **`input::Dict{<:Resource,<:Real}`** は、変換値 `Real` を持つ入力 [`Resource`](@ref) です。
  * **`output::Dict{<:Resource,<:Real}`** は、変換値 `Real` を持つ生成された [`Resource`](@ref) です。出力値は計算に利用されないため、リンクおよび格納された [`Resource`](@ref) にのみ関連します。
  * **`data::Vector{<:Data}`** は追加データ (*例：* 投資用) です。フィールド `data` はコンストラクタの使用によって条件付きです。
