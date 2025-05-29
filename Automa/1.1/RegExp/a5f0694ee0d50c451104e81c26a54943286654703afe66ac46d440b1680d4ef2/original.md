```
onfinal!(re::RE, a::Union{Symbol, Vector{Symbol}}) -> re
```

Set action(s) `a` to occur when the last byte of regex `re`. If `re` does not have a definite final byte, e.g. `re"a(bc)*"`, where more "bc" can always be added, compiling the regex will error after setting a final action. If multiple actions are set by passing a vector, execute the actions in order.

See also: [`onenter!`](@ref), [`onall!`](@ref), [`onexit!`](@ref)

# Example

```julia
julia> regex = re"ab?c";

julia> regex2 = onfinal!(regex, :entering_last_byte);

julia> regex === regex2
true

julia> compile(onfinal!(re"ab?c*", :does_not_work))
ERROR: [...]
```
