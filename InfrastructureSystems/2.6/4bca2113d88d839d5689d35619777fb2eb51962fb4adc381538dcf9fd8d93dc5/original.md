```julia
make_selector(
    filter_func::Function,
    component_type::Type{<:InfrastructureSystems.InfrastructureSystemsComponent};
    name,
    groupby
) -> InfrastructureSystems.FilterComponentSelector

```

Make a [`ComponentSelector`](@ref) from a filter function and a type of component. The filter function must accept instances of `component_type` as a sole argument and return a `Bool`. Optionally provide a grouping behavior and/or name for the selector. Selectors constructed this way point to all the components of the given type that satisfy the filter function, grouped by the `groupby` argument (see the base [`make_selector`](@ref) documentation).

# Arguments

  * `filter_func::Function`: the filter function to apply to components
  * `component_type::Type{<:InfrastructureSystemsComponent}`: the type of component to select
  * `groupby::Union{Symbol, Function} = :each`: the grouping behavior (see the base [`make_selector`](@ref) documentation)
  * `name::Union{String, Nothing} = nothing`: the name of the selector; if not provided, one will be constructed automatically

# Examples

```julia
sel1 = make_selector(RenewableDispatch, x -> get_prime_mover_type(x) == PrimeMovers.PVe)
sel2 = make_selector(RenewableDispatch, x -> get_prime_mover_type(x) == PrimeMovers.PVe; groupby = :all)
sel3 = make_selector(RenewableDispatch, x -> get_prime_mover_type(x) == PrimeMovers.PVe; name = "my_selector")
```

See also: [`make_selector`](@ref) unified function documentation
