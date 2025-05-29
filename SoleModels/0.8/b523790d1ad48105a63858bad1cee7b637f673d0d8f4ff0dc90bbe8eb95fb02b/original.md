```
printmodel(io::IO, m::AbstractModel; kwargs...)
displaymodel(m::AbstractModel; kwargs...)
```

print or returnPa string representation of model `m`.

# Arguments

  * `header::Bool = true`: when set to `true`, a header is printed, displaying the `info` structure for `m`;
  * `show_subtree_info::Bool = false`: when set to `true`, the header is printed for models in the sub-tree of `m`;
  * `show_metrics::Bool = false`: when set to `true`, performance metrics at each point of the subtree are shown, whenever they are available in the `info` structure;
  * `max_depth::Union{Nothing,Int} = nothing`: when it is an `Int`, models in the sub-tree with a depth higher than `max_depth` are ellipsed with "...";
  * `syntaxstring_kwargs::NamedTuple = (;)`: kwargs to be passed to `syntaxstring` for formatting logical formulas.

See also [`syntaxstring`](@ref), [`AbstractModel`](@ref).
