```
struct_name_plain(def)
```

Plain constructor name. See also [`struct_name_without_inferable`](@ref).

# Example

```julia
julia> def = @expr JLKwStruct struct Foo{N, Inferable}
    x::Inferable = 1
end

julia> struct_name_plain(def)
:(Foo{N, Inferable})
```
