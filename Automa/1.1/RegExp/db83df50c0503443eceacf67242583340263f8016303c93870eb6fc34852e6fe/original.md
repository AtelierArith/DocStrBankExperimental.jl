```
onenter!(re::RE, a::Union{Symbol, Vector{Symbol}}) -> re
```

Set action(s) `a` to occur when reading the first byte of regex `re`. If multiple actions are set by passing a vector, execute the actions in order.

See also: [`onexit!`](@ref), [`onall!`](@ref), [`onfinal!`](@ref)

# Example

```julia
julia> regex = re"ab?c*";

julia> regex2 = onenter!(regex, :entering_regex);

julia> regex === regex2
true
```
