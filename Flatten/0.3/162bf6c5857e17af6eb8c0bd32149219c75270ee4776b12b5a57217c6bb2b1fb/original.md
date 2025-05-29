```
fieldtypeflatten(obj, args...)
```

Flatten the field types of an object. Args are passed to [`metaflatten`](@ref).

# Examples

```jldoctest
julia> using Flatten

julia> struct Foo{A,B,C}
           a::A
           b::B
           c::C
       end

julia> fieldtypeflatten(Foo(1.0, :two, "Three"), Union{Real,String})
(Float64, String)
```
