```
generate_design(c::AbstractCircuit, tuple_set::Vector{Vector{Int}}; kwargs...)
generate_design(c::AbstractCircuit, tuple_set_data::TupleSetData; kwargs...)
generate_design(c::AbstractCircuit, d::Design; kwargs...)
generate_design(c::AbstractCircuit; kwargs...)
```

[`Design`](@ref) オブジェクトを返し、実験デザインを説明するすべての関連情報を含み、デザイン行列を含みます。

# 引数

  * `c::AbstractCircuit`: デザイン行列を生成する回路。
  * `tuple_set::Vector{Vector{Int}}`: 実験デザインを生成するために使用される回路層を配置するタプルセット。
  * `tuple_set_data::TupleSetData`: タプルセットを生成する [`TupleSetData`](@ref) オブジェクト。
  * `d::Design`: 回路 `c` のデザインを生成するために使用されるパラメータを持つ古いデザインオブジェクト。

# キーワード引数

  * `shot_weights::Union{Vector{Float64}, Nothing} = nothing`: セット内の各タプルのショットウェイトで、合計が1になる必要があります。`nothing` の場合、デフォルトのショットウェイトが自動的に生成されます。
  * `N_warn::Integer = 10^5`: 特定のキーワード引数の選択についてユーザーに警告する回路の固有値の数。
  * `full_covariance::Bool = (c.gate_data.N < N_warn ? true : false)`: `true` の場合、完全な共分散行列を構築するためのパラメータを生成し、`false` の場合は対角線上の項を構築するためのパラメータのみを生成します。
  * `add_circuit::Bool = false`: タプルセットデータが提供されていない場合、回路自体がリピートタプルセットに追加されます。
  * `repeat_points::Integer = 1`: タプルセットデータが提供されていない場合、各リピート番号が `repeat_points` のリピート番号を持つように増強されます。
  * `weight_experiments::Bool = true`: タプルのショットウェイトをそのタプルの実験数で重み付けするかどうか。
  * `diagnostics::Bool = false`: 診断情報を印刷するかどうか。
  * `save_data::Bool = false`: デザインデータを保存するかどうか。
