```
onall!(re::RE, a::Union{Symbol, Vector{Symbol}}) -> re
```

Set action(s) `a` to occur when reading any byte part of the regex `re`. If multiple actions are set by passing a vector, execute the actions in order.

See also: [`onenter!`](@ref), [`onexit!`](@ref), [`onfinal!`](@ref)

# Example

```julia
julia> regex = re"ab?c*";

julia> regex2 = onall!(regex, :reading_re_byte);

julia> regex === regex2
true
```
