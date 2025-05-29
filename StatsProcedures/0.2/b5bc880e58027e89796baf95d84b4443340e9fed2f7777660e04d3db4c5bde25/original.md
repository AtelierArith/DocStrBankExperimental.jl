```
StatsSpec{T<:AbstractStatsProcedure}
```

Specification for a statistical procedure of type `T`.

An instance of `StatsSpec` is callable and its fields provide all information necessary for conducting the procedure. An optional name for the specification can be specified.

# Fields

  * `name::String`: a name for the specification (takes `""` if not specified).
  * `args::NamedTuple`: arguments for the [`StatsStep`](@ref)s in `T` (default values are merged into `args` if not found in `args`).

# Methods

```
(sp::StatsSpec{T})(; verbose::Union{Bool,IO}=false, keep=nothing, keepall::Bool=false)
```

Execute the procedure of type `T` with the arguments specified in `args`. By default, a dedicated result object for `T` is returned if it is available. Otherwise, the last value returned by the last [`StatsStep`](@ref) is returned.

## Keywords

  * `verbose::Union{Bool,IO}=false`: print the name of each step to `stdout` or the specified `IO` stream when it is called.
  * `keep=nothing`: names (of type `Symbol`) of additional objects to be returned.
  * `keepall::Bool=false`: return all objects returned by each step.
