```julia
struct VariableSummary <: DistributedFactorGraphs.AbstractDFGVariable
```

Summary variable structure for a DistributedFactorGraph variable.

---

Fields:

  * `id::Union{Nothing, Base.UUID}`: The ID for the variable
  * `label::Symbol`: Variable label, e.g. :x1. Accessor: [`getLabel`](@ref)
  * `timestamp::TimeZones.ZonedDateTime`: Variable timestamp. Accessors: [`getTimestamp`](@ref), [`setTimestamp`](@ref)
  * `tags::Set{Symbol}`: Variable tags, e.g [:POSE, :VARIABLE, and :LANDMARK]. Accessors: [`getTags`](@ref), [`mergeTags!`](@ref), and [`removeTags!`](@ref)
  * `ppeDict::Dict{Symbol, <:DistributedFactorGraphs.AbstractPointParametricEst}`: Dictionary of parametric point estimates keyed by solverDataDict keys Accessors: [`addPPE!`](@ref), [`updatePPE!`](@ref), and [`deletePPE!`](@ref)
  * `variableTypeName::Symbol`: Symbol for the variableType for the underlying variable. Accessor: [`getVariableType`](@ref)
  * `dataDict::Dict{Symbol, DistributedFactorGraphs.BlobEntry}`: Dictionary of large data associated with this variable. Accessors: [`addBlobEntry!`](@ref), [`getBlobEntry`](@ref), [`updateBlobEntry!`](@ref), and [`deleteBlobEntry!`](@ref)
