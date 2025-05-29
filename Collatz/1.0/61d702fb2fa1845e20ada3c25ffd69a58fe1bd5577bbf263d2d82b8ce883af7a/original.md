```
tree_graph(initial_value, max_orbit_distance; P=2, a=3, b=1, __cycle_prevention=nothing)
```

Returns nested dictionaries that model the directed tree graph up to a maximum nesting of max*orbit*distance, with the initial_value as the root.

# Args

  * `initial_value::Integer`: The root value of the directed tree graph.
  * `max_orbit_distance::Integer`: Maximum amount of times to iterate the reverse   function. There is no natural termination to populating the tree graph, equivalent   to the termination of hailstone sequences or stopping time attempts, so this is not   an optional argument like max*stopping*time / max*total*stopping_time, as it is the   intended target of orbits to obtain, rather than a limit to avoid uncapped computation.

# Kwargs

  * `P::Integer=2`: Modulus used to devide n, iff n is equivalent to (0 mod P).
  * `a::Integer=3`: Factor by which to multiply n.
  * `b::Integer=1`: Value to add to the scaled value of n.

# Internal Kwargs

  * `__cycle_prevention::Union{Set{Integer},Nothing}=nothing`: Used to prevent cycles   from precipitatingby keeping track of all values added across previous nest depths.

# Examples

```
julia> print(tree_graph(1, 3))
Dict{Int64, Dict{Any, Any}}(1 => Dict(2 => Dict{Any, Any}(4 => Dict{Any, Any}(Collatz._CC.CYCLE_INIT => 1, 8 => Dict{Any, Any}()))))
```

```
julia> print(tree_graph(4, 3))
Dict{Int64, Dict{Any, Any}}(4 => Dict(8 => Dict{Any, Any}(16 => Dict{Any, Any}(5 => Dict{Any, Any}(), 32 => Dict{Any, Any}())), 1 => Dict{Any, Any}(2 => Dict{Any, Any}(Collatz._CC.CYCLE_INIT => 4))))
```
