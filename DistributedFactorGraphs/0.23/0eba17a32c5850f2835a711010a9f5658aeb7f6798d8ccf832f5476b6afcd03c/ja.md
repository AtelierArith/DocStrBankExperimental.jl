```julia
struct DFGFactor{T, N} <: DistributedFactorGraphs.AbstractDFGFactor
```

DistributedFactorGraph因子の完全な因子構造。

DevNotes

  * TODO フィールドの順序をSkeleton、Summary、DFGFactorに一貫性を持たせる

      * 例えば、timestampは後のフィールドであるべきです。

    ---

フィールド:

  * `id::Union{Nothing, Base.UUID}`: 因子のID
  * `label::Symbol`: 因子ラベル、例: :x1f1。アクセサ: [`getLabel`](@ref)
  * `tags::Set{Symbol}`: 因子タグ、例: [:FACTOR]。アクセサ: [`getTags`](@ref)、[`mergeTags!`](@ref)、および[`removeTags!`](@ref)
  * `_variableOrderSymbols::NTuple{N, Symbol} where N`: 隣接変数の順序の内部キャッシュ。これは内部値であるため、リストを取得するにはgetVariableOrderを使用してください。アクセサ: [`getVariableOrder`](@ref)
  * `timestamp::TimeZones.ZonedDateTime`: 変数のタイムスタンプ。アクセサ: [`getTimestamp`](@ref)、[`setTimestamp`](@ref)
  * `nstime::Dates.Nanosecond`: ナノ秒の時間、タイムスタンプの解像度を高めるため（サブ秒情報のみ）
  * `solverData::Base.RefValue{DistributedFactorGraphs.GenericFunctionNodeData{T}} where T`: ソルバーデータ。アクセサ: [`getSolverData`](@ref)、[`setSolverData!`](@ref)
  * `solvable::Base.RefValue{Int64}`: 因子の解決可能フラグ。アクセサ: [`getSolvable`](@ref)、[`setSolvable!`](@ref)
  * `smallData::Dict{Symbol, Union{Bool, Float64, Int64, Vector{Bool}, Vector{Float64}, Vector{Int64}, Vector{String}, String}}`: この変数に関連付けられた小さなデータの辞書。アクセサ: [`getSmallData`](@ref)、[`setSmallData!`](@ref)
