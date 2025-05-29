```
CO2Source <: Source
```

CO₂ `Source` ノード。これは [`RefSource`](@extref EnergyModelsBase.RefSource) との唯一の違いは、CO₂ をアウトレットとして許可することです。

# フィールド

  * **`id`** はノードの名前/識別子です。
  * **`cap::TimeProfile`** は設置された容量です。
  * **`opex_var::TimeProfile`** は生産されたエネルギー単位あたりの変動運用コストです。
  * **`opex_fixed::TimeProfile`** は固定運用コストです。
  * **`output::Dict{<:Resource, <:Real}`** は変換値 `Real` を持つ生成された `Resource` です。
  * **`data::Array{<:Data}`** は追加データ（例：投資用）です。フィールド `data` はコンストラクタの使用によって条件付きです。
