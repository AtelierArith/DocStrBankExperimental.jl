```julia
struct FactorSummary <: DistributedFactorGraphs.AbstractDFGFactor
```

読み取り専用の要約因子構造体で、DistributedFactorGraph因子のためのものです。

---

フィールド:

  * `id::Union{Nothing, Base.UUID}`: 因子のID
  * `label::Symbol`: 因子のラベル、例: :x1f1。アクセサ: [`getLabel`](@ref)
  * `tags::Set{Symbol}`: 因子のタグ、例: [:FACTOR]。アクセサ: [`getTags`](@ref), [`mergeTags!`](@ref), および [`removeTags!`](@ref)
  * `_variableOrderSymbols::Vector{Symbol}`: 隣接変数の順序の内部キャッシュ。内部値であるため、リストを取得するにはlistNeighborsを使用してください。アクセサ: [`getVariableOrder`](@ref)
  * `timestamp::TimeZones.ZonedDateTime`: 変数のタイムスタンプ。アクセサ: [`getTimestamp`](@ref)
