```julia
mutable struct PackedVariableNodeData
```

DFGVariablesをシリアライズするためのPacked VariableNodeData構造体。

---

フィールド:

  * `id::Union{Nothing, Base.UUID}`
  * `vecval::Vector{Float64}`
  * `dimval::Int64`
  * `vecbw::Vector{Float64}`
  * `dimbw::Int64`
  * `BayesNetOutVertIDs::Vector{Symbol}`
  * `dimIDs::Vector{Int64}`
  * `dims::Int64`
  * `eliminated::Bool`
  * `BayesNetVertID::Symbol`
  * `separator::Vector{Symbol}`
  * `variableType::String`
  * `initialized::Bool`
  * `infoPerCoord::Vector{Float64}`
  * `ismargin::Bool`
  * `dontmargin::Bool`
  * `solveInProgress::Int64`
  * `solvedCount::Int64`
  * `solveKey::Symbol`
  * `covar::Vector{Float64}`
  * `_version::String`
