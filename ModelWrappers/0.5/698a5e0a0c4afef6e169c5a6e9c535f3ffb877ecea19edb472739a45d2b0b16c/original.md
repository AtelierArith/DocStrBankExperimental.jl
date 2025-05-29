```julia
mutable struct ModelWrapper{M<:(Union{ModelWrappers.ModelName, P} where P), A<:NamedTuple, C<:NamedTuple, B<:ModelWrappers.ParameterInfo} <: BaytesCore.AbstractModelWrapper
```

Baytes Model struct.

Contains information about current Model value, name, and information, see also [`ParameterInfo`](@ref).

# Fields

  * `val::NamedTuple`: Current Model values as NamedTuple - works with Nested Tuples.
  * `arg::NamedTuple`: Supplementary arguments for log target function that are fixed and dont need to be stored in a trace.
  * `info::ModelWrappers.ParameterInfo`: Information about parameter distributions, transformations and constraints, see [`ParameterInfo`](@ref).
  * `id::Union{ModelWrappers.ModelName, P} where P`: Model id, per default BaseModel. Useful for dispatching ModelWrapper struct.
