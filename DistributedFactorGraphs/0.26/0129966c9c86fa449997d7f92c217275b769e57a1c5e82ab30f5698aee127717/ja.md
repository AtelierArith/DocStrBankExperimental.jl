```julia
struct VariableSummary <: DistributedFactorGraphs.AbstractDFGVariable
```

DistributedFactorGraph変数のためのサマリ変数構造。

---

フィールド:

  * `id::Union{Nothing, Base.UUID}`: 変数のID
  * `label::Symbol`: 変数ラベル、例: :x1。アクセサ: [`getLabel`](@ref)
  * `timestamp::TimeZones.ZonedDateTime`: 変数のタイムスタンプ。アクセサ: [`getTimestamp`](@ref), [`setTimestamp`](@ref)
  * `tags::Set{Symbol}`: 変数のタグ、例: [:POSE, :VARIABLE, および :LANDMARK]。アクセサ: [`getTags`](@ref), [`mergeTags!`](@ref), および [`removeTags!`](@ref)
  * `ppeDict::Dict{Symbol, <:DistributedFactorGraphs.AbstractPointParametricEst}`: solverDataDictキーによってキー付けされたパラメトリックポイント推定の辞書。アクセサ: [`addPPE!`](@ref), [`updatePPE!`](@ref), および [`deletePPE!`](@ref)
  * `variableTypeName::Symbol`: 基本変数のためのvariableTypeのシンボル。アクセサ: [`getVariableType`](@ref)
  * `dataDict::Dict{Symbol, DistributedFactorGraphs.BlobEntry}`: この変数に関連する大きなデータの辞書。アクセサ: [`addBlobEntry!`](@ref), [`getBlobEntry`](@ref), [`updateBlobEntry!`](@ref), および [`deleteBlobEntry!`](@ref)
