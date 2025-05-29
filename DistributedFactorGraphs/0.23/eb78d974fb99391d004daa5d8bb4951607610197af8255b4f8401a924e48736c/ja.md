```julia
struct DFGVariable{T<:DistributedFactorGraphs.InferenceVariable, P, N} <: DistributedFactorGraphs.AbstractDFGVariable
```

DistributedFactorGraph変数の完全な変数構造。

---

フィールド:

  * `id::Union{Nothing, Base.UUID}`: 変数のID
  * `label::Symbol`: 変数ラベル、例: :x1。アクセサ: [`getLabel`](@ref)
  * `timestamp::TimeZones.ZonedDateTime`: 変数のタイムスタンプ。アクセサ: [`getTimestamp`](@ref), [`setTimestamp`](@ref)
  * `nstime::Dates.Nanosecond`: ユーザーが理解できるエポック（すなわち、unixエポック、ロボットの起動時間など）からのナノ秒
  * `tags::Set{Symbol}`: 変数のタグ、例: [:POSE, :VARIABLE, :LANDMARK]。アクセサ: [`getTags`](@ref), [`mergeTags!`](@ref), [`removeTags!`](@ref)
  * `ppeDict::Dict{Symbol, DistributedFactorGraphs.AbstractPointParametricEst}`: solverDataDictキーでキー付けされたパラメトリックポイント推定の辞書。アクセサ: [`addPPE!`](@ref), [`updatePPE!`](@ref), [`deletePPE!`](@ref)
  * `solverDataDict::Dict{Symbol, DistributedFactorGraphs.VariableNodeData{T, P, N}} where {T<:DistributedFactorGraphs.InferenceVariable, P, N}`: ソルバーデータの辞書。get呼び出しでソルバーキーが指定された場合、すべての解のサブセットである可能性があります。アクセサ: [`addVariableSolverData!`](@ref), [`updateVariableSolverData!`](@ref), [`deleteVariableSolverData!`](@ref)
  * `smallData::Dict{Symbol, Union{Bool, Float64, Int64, Vector{Bool}, Vector{Float64}, Vector{Int64}, Vector{String}, String}}`: この変数に関連する小さなデータの辞書。アクセサ: [`getSmallData`](@ref), [`setSmallData!`](@ref)
  * `dataDict::Dict{Symbol, DistributedFactorGraphs.BlobEntry}`: この変数に関連する大きなデータの辞書。アクセサ: [`addBlobEntry!`](@ref), [`getBlobEntry`](@ref), [`updateBlobEntry!`](@ref), [`deleteBlobEntry!`](@ref)
  * `solvable::Base.RefValue{Int64}`: 変数の解決可能フラグ。アクセサ: [`getSolvable`](@ref), [`setSolvable!`](@ref)
