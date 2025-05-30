```
Union{Types...}
```

A type union is an abstract type which includes all instances of any of its argument types. The empty union [`Union{}`](@ref) is the bottom type of Julia.

# Examples

```jldoctest
julia> IntOrString = Union{Int,AbstractString}
Union{Int64, AbstractString}

julia> 1 isa IntOrString
true

julia> "Hello!" isa IntOrString
true

julia> 1.0 isa IntOrString
false
```
