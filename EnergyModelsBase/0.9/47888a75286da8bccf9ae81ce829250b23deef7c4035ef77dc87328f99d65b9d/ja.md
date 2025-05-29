```
struct RefSource <: Source
```

参照 [`Source`](@ref) ノード。参照 [`Source`](@ref) ノードは、フィールド `input` で変換値 1 に正規化された時間変動容量を許可します。投資を含める場合、`TimeProfile` として使用できるのは `FixedProfile` または `StrategicProfile` のみです。

# フィールド

  * **`id`** はノードの名前/識別子です。
  * **`cap::TimeProfile`** は設置された容量です。
  * **`opex_var::TimeProfile`** は変数 `:cap_use` を通じて容量使用ごとの可変運営費です。
  * **`opex_fixed::TimeProfile`** は変数 `:cap_inst` を通じて設置された容量ごとの固定運営費です。
  * **`output::Dict{<:Resource,<:Real}`** は変換値 `Real` を持つ生成された [`Resource`](@ref) です。
  * **`data::Vector{<:Data}`** は追加データ (*例：* 投資用) です。フィールド `data` はコンストラクタの使用によって条件付きです。
