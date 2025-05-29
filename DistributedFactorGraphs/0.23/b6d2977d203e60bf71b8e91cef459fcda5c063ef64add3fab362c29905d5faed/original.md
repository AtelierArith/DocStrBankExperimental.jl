```julia
struct DFGFactorSummary <: DistributedFactorGraphs.AbstractDFGFactor
```

Read-only summary factor structure for a DistributedFactorGraph factor.

---

Fields:

  * `id::Union{Nothing, Base.UUID}`: The ID for the factor
  * `label::Symbol`: Factor label, e.g. :x1f1. Accessor: [`getLabel`](@ref)
  * `tags::Set{Symbol}`: Factor tags, e.g [:FACTOR]. Accessors: [`getTags`](@ref), [`mergeTags!`](@ref), and [`removeTags!`](@ref)
  * `_variableOrderSymbols::Vector{Symbol}`: Internal cache of the ordering of the neighbor variables. Rather use listNeighbors to get the list as this is an internal value. Accessors: [`getVariableOrder`](@ref)
  * `timestamp::TimeZones.ZonedDateTime`: Variable timestamp. Accessors: [`getTimestamp`](@ref)
