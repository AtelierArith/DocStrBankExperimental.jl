```julia
struct DFGVariable{T<:DistributedFactorGraphs.InferenceVariable, P, N} <: DistributedFactorGraphs.AbstractDFGVariable
```

Complete variable structure for a DistributedFactorGraph variable.

---

Fields:

  * `id::Union{Nothing, Base.UUID}`: The ID for the variable
  * `label::Symbol`: Variable label, e.g. :x1. Accessor: [`getLabel`](@ref)
  * `timestamp::TimeZones.ZonedDateTime`: Variable timestamp. Accessors: [`getTimestamp`](@ref), [`setTimestamp`](@ref)
  * `nstime::Dates.Nanosecond`: Nanoseconds since a user-understood epoch (i.e unix epoch, robot boot time, etc.)
  * `tags::Set{Symbol}`: Variable tags, e.g [:POSE, :VARIABLE, and :LANDMARK]. Accessors: [`getTags`](@ref), [`mergeTags!`](@ref), and [`removeTags!`](@ref)
  * `ppeDict::Dict{Symbol, DistributedFactorGraphs.AbstractPointParametricEst}`: Dictionary of parametric point estimates keyed by solverDataDict keys Accessors: [`addPPE!`](@ref), [`updatePPE!`](@ref), and [`deletePPE!`](@ref)
  * `solverDataDict::Dict{Symbol, DistributedFactorGraphs.VariableNodeData{T, P, N}} where {T<:DistributedFactorGraphs.InferenceVariable, P, N}`: Dictionary of solver data. May be a subset of all solutions if a solver key was specified in the get call. Accessors: [`addVariableSolverData!`](@ref), [`updateVariableSolverData!`](@ref), and [`deleteVariableSolverData!`](@ref)
  * `smallData::Dict{Symbol, Union{Bool, Float64, Int64, Vector{Bool}, Vector{Float64}, Vector{Int64}, Vector{String}, String}}`: Dictionary of small data associated with this variable. Accessors: [`getSmallData`](@ref), [`setSmallData!`](@ref)
  * `dataDict::Dict{Symbol, DistributedFactorGraphs.BlobEntry}`: Dictionary of large data associated with this variable. Accessors: [`addBlobEntry!`](@ref), [`getBlobEntry`](@ref), [`updateBlobEntry!`](@ref), and [`deleteBlobEntry!`](@ref)
  * `solvable::Base.RefValue{Int64}`: Solvable flag for the variable. Accessors: [`getSolvable`](@ref), [`setSolvable!`](@ref)
