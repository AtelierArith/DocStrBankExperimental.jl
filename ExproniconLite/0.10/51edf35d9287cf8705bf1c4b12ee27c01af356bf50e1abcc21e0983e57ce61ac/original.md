```
struct_name_without_inferable(def; leading_inferable::Bool=true)
```

Constructor name that assume some of the type variables is inferred. See also [`struct_name_plain`](@ref). The kwarg `leading_inferable` can be used to configure whether to preserve the leading inferable type variables, the default is `true` to be consistent with the default julia constructors.

# Example

```julia
julia> def = @expr JLKwStruct struct Foo{N, Inferable}
    x::Inferable = 1
end

julia> struct_name_without_inferable(def)
:(Foo{N})

julia> def = @expr JLKwStruct struct Foo{Inferable, NotInferable}
    x::Inferable
end

julia> struct_name_without_inferable(def; leading_inferable=true)
:(Foo{Inferable, NotInferable})

julia> struct_name_without_inferable(def; leading_inferable=false)
:(Foo{NotInferable})
```
