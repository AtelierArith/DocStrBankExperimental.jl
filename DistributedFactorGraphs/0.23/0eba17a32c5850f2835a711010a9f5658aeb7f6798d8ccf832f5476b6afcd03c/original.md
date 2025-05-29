```julia
struct DFGFactor{T, N} <: DistributedFactorGraphs.AbstractDFGFactor
```

Complete factor structure for a DistributedFactorGraph factor.

DevNotes

  * TODO make consistent the order of fields skeleton Skeleton, Summary, thru DFGFactor

      * e.g. timestamp should be a later field.

    ---

Fields:

  * `id::Union{Nothing, Base.UUID}`: The ID for the factor
  * `label::Symbol`: Factor label, e.g. :x1f1. Accessor: [`getLabel`](@ref)
  * `tags::Set{Symbol}`: Factor tags, e.g [:FACTOR]. Accessors: [`getTags`](@ref), [`mergeTags!`](@ref), and [`removeTags!`](@ref)
  * `_variableOrderSymbols::NTuple{N, Symbol} where N`: Internal cache of the ordering of the neighbor variables. Rather use getVariableOrder to get the list as this is an internal value. Accessors: [`getVariableOrder`](@ref)
  * `timestamp::TimeZones.ZonedDateTime`: Variable timestamp. Accessors: [`getTimestamp`](@ref), [`setTimestamp`](@ref)
  * `nstime::Dates.Nanosecond`: Nano second time, for more resolution on timestamp (only subsecond information)
  * `solverData::Base.RefValue{DistributedFactorGraphs.GenericFunctionNodeData{T}} where T`: Solver data. Accessors: [`getSolverData`](@ref), [`setSolverData!`](@ref)
  * `solvable::Base.RefValue{Int64}`: Solvable flag for the factor. Accessors: [`getSolvable`](@ref), [`setSolvable!`](@ref)
  * `smallData::Dict{Symbol, Union{Bool, Float64, Int64, Vector{Bool}, Vector{Float64}, Vector{Int64}, Vector{String}, String}}`: Dictionary of small data associated with this variable. Accessors: [`getSmallData`](@ref), [`setSmallData!`](@ref)
