```
struct RefSink <: Sink
```

参照 [`Sink`](@ref) ノード。このノードはフィールド `cap` によって与えられる需要に対応しています。フィールド `penalty` に導入されるペナルティは、余剰と不足の両方に対して変数 OPEX に影響を与えます。

# フィールド

  * **`id`** はノードの名前/識別子です。
  * **`cap::TimeProfile`** は需要です。
  * **`penalty::Dict{Symbol,<:TimeProfile}`** は余剰または不足に対するペナルティです。この辞書はフィールド `:surplus` と `:deficit` を必要とします。
  * **`input::Dict{<:Resource,<:Real}`** は変換値 `Real` を持つ入力 [`Resource`](@ref) です。
  * **`data::Vector{<:Data}`** は追加データ (*例*: 投資用) です。フィールド `data` はコンストラクタの使用によって条件付きです。
