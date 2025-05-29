```
mutable struct BSTModel <: AbstractBSTModel
```

BSTモデルオブジェクトのための可変保持構造体。このオブジェクトは、モデルをシミュレートするために必要なすべてのデータを格納するために使用されます。このオブジェクトは、モデルをシミュレートするために`evaluate`関数に渡されます。`BSTModel`オブジェクトは、`build`関数を使用して作成されます。

### フィールド

  * `number_of_dynamic_states::Int64`: モデル内の動的状態の数。
  * `number_of_static_states::Int64`: モデル内の静的状態の数。
  * `list_of_dynamic_species::Array{String,1}`: モデル内の動的種のリスト。
  * `list_of_static_species::Array{String,1}`: モデル内の静的種のリスト。
  * `list_of_reactions::Array{String,1}`: モデル内の反応のリスト。
  * `total_species_list::Array{String,1}`: モデル内のすべての種のリスト。
  * `static_factors_array::Array{Float64,1}`: モデル内の静的因子のリスト。
  * `initial_condition_array::Array{Float64,1}`: 動的状態の初期条件のリスト。
  * `S::Array{Float64,2}`: ストイキオメトリ行列。
  * `G::Array{Float64,2}`: 指数行列。
  * `α::Array{Float64,1}`: 反応速度定数ベクトル。

### メタデータフィールド

  * `author::String`: モデルの著者。
  * `version::String`: モデルのバージョン。
  * `date::String`: モデルが作成された日付。
  * `description::String`: モデルの説明。
