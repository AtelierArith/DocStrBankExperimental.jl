```
add_sparsity_entries!(
    sp::AbstractSparsityPattern,
    dh::DofHandler,
    ch::Union{ConstraintHandler, Nothing} = nothing;
    topology = nothing,
    keep_constrained::Bool = true,
    coupling = nothing,
    interface_coupling = nothing,
)
```

Convenience method for doing the common task of calling [`add_cell_entries!`](@ref), [`add_interface_entries!`](@ref), and [`add_constraint_entries!`](@ref), depending on what arguments are passed:

  * `add_cell_entries!` is always called
  * `add_interface_entries!` is called if `topology` is provided (i.e. not `nothing`)
  * `add_constraint_entries!` is called if the ConstraintHandler is provided

For more details about arguments and keyword arguments, see the respective functions.
