```
ImpostorTemplate(formats::Union{T, S, Vector{Union{T, S}}}) where {T<:AbstractString, S<:Symbol}
```

Struct storing the `formats` used to generate new tables. Each of the elements in `formats` maps to a generator function exported by Impostor. This struct is later used as a *functor* in order to generate data, that is, after instantiating a new `ImpostorTemplate` object, this object will be called providing arguments in order to generate the data entries.

# Parameters

  * `formats` (`String`, `Symbol` or `Vector{Union{String, Symbol}}`): table output format specified in terms of generator functions to be used in each column (see examples below).

# Examples

```@repl
julia> imp = ImpostorTemplate("firstname")
ImpostorTemplate([:firstname])

julia> imp = ImpostorTemplate(:firstname)
ImpostorTemplate([:firstname])

julia> imp = ImpostorTemplate(["firstname"])
ImpostorTemplate([:firstname])

julia> imp = ImpostorTemplate([:firstname])
ImpostorTemplate([:firstname])
```
