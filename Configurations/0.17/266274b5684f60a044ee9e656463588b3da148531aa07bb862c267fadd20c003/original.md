```
to_dict(::Type{T}, x, option::ToDictOption) where T
```

Convert `x` when `x` is inside an option type `T`. `option` is a set of options to determine the conversion behaviour. this can be overloaded to change the behaviour of `to_dict(x; kw...)`.

```
to_dict(::Type{T}, x) where T
```

One can also use the 2-arg version when `x` is not or does not contain an option type for convenience.

# Example

The following is a builtin overload to handle list of options.

```julia
function Configurations.to_dict(::Type{T}, x::Vector, option::ToDictOption) where T
    if is_option(eltype(x))
        return map(p->to_dict(T, p, include_defaults), x)
    else
        return x
    end
end
```

The following overloads the 2-arg `to_dict` to convert all `VersionNumber` to a `String` for all kinds of option types.

```julia
Configurations.to_dict(::Type, x::VersionNumber) = string(x)
```
