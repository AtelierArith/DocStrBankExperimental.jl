```
onexit!(re::RE, a::Union{Symbol, Vector{Symbol}}) -> re
```

Set action(s) `a` to occur when reading the first byte no longer part of regex `re`, or if experiencing an expected end-of-file. If multiple actions are set by passing a vector, execute the actions in order.

See also: [`onenter!`](@ref), [`onall!`](@ref), [`onfinal!`](@ref)

# Example

```julia
julia> regex = re"ab?c*";

julia> regex2 = onexit!(regex, :exiting_regex);

julia> regex === regex2
true
```
