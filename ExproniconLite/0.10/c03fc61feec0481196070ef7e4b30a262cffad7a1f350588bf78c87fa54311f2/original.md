```
name_only(ex)
```

Remove everything else leaving just names, currently supports function calls, type with type variables, subtype operator `<:` and type annotation `::`.

# Example

```julia
julia> using Expronicon

julia> name_only(:(sin(2)))
:sin

julia> name_only(:(Foo{Int}))
:Foo

julia> name_only(:(Foo{Int} <: Real))
:Foo

julia> name_only(:(x::Int))
:x
```
