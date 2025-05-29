```
@suffix T [= ....]
```

Defines a [`SuffixConverter`](@ref) for type `T` with the same name, prefixed by an underscore. For convenience, it can also accept an expression which defines `T` itself.`

# Examples

Using an already-defined type

```julia
function addhalf(x::FT) where {FT}
    @suffix FT
    return x + 0.5_FT
end
```

Defining the type inline

```julia
function addhalf(x)
    @suffix FT = typeof(FT)
    return x + 0.5_FT
end
```
