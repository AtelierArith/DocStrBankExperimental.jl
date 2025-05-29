```
to_toml([f::Function], io::IO, option; sorted=false, by=identity, kw...)
```

Convert an instance `option` of option type to TOML and write it to `IO`. See [`to_dict`](@ref) for other valid keyword options. See also `TOML.print` in the stdlib for the explaination of `sorted`, `by` and `f`.

# Exclude `nothing`

In TOML specification, there is [no null type](https://github.com/toml-lang/toml/issues/802). One should exclude the field if it is not specified (of value `nothing` in Julia). In `to_toml` the option `exclude_nothing` is always `true`.

In most cases, `nothing` is used with another type to denote optional or not specified field, thus one should always put a default value `nothing` to the option struct, e.g

One should define

```julia
@option struct OptionX
    a::Union{Nothing, Int} = nothing
    b::Maybe{Int} = nothing
end
```

Here `Maybe{T}` is a convenient alias of `Union{Nothing, T}`.
