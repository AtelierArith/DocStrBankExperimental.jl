jldoctest     fieldnameflatten(obj, args...)

Flatten the field names of an object. Args are passed to [`metaflatten`](@ref).

# Examples

```jldoctest
julia> using Flatten

julia> struct Foo{A,B,C}
           a::A
           b::B
           c::C
       end

julia> fieldnameflatten(Foo(1, 2, 3))
(:a, :b, :c)
```
