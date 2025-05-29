```julia
struct DFGFactorSummary <: DistributedFactorGraphs.AbstractDFGFactor
```

DistributedFactorGraph因子の読み取り専用要約因子構造。

---

フィールド:

  * `id::Union{Nothing, Base.UUID}`: 因子のID
  * `label::Symbol`: 因子ラベル、例: :x1f1。アクセサ: [`getLabel`](@ref)
  * `tags::Set{Symbol}`: 因子タグ、例: [:FACTOR]。アクセサ: [`getTags`](@ref), [`mergeTags!`](@ref), および [`removeTags!`](@ref)
  * `_variableOrderSymbols::Vector{Symbol}`: 隣接変数の順序の内部キャッシュ。これは内部値であるため、listNeighborsを使用してリストを取得することをお勧めします。アクセサ: [`getVariableOrder`](@ref)
  * `timestamp::TimeZones.ZonedDateTime`: 変数のタイムスタンプ。アクセサ: [`getTimestamp`](@ref)
