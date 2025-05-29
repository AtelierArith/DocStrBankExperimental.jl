```
struct RefNetworkNode <: NetworkNode
```

参照 [`NetworkNode`](@ref) ノード。`RefNetworkNode` は、利用可能な容量に従って、`input` [`Resource`](@ref) から出力 [`Resource`](@ref) への線形で時間に依存しない変換率を利用します。容量は、フィールド `input` と `output` において変換値 1 に正規化されています。

# フィールド

  * **`id`** はノードの名前/識別子です。
  * **`cap::TimeProfile`** は設置された容量です。
  * **`opex_var::TimeProfile`** は変数 `:cap_use` を通じて容量使用ごとの可変運営費用です。
  * **`opex_fixed::TimeProfile`** は変数 `:cap_inst` を通じて設置された容量ごとの固定運営費用です。
  * **`input::Dict{<:Resource,<:Real}`** は変換値 `Real` を持つ入力 [`Resource`](@ref) です。
  * **`output::Dict{<:Resource,<:Real}`** は変換値 `Real` を持つ生成された [`Resource`](@ref) です。
  * **`data::Vector{Data}`** は追加データ (*例：* 投資用) です。フィールド `data` はコンストラクタの使用によって条件付きです。
