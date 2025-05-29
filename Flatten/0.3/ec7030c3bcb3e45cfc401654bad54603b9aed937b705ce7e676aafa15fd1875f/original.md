```
parenttypeflatten(obj, args...)
```

Flatten the parent type of an object. Args are passed to [`metaflatten`](@ref).

# Examples

```jldoctest
julia> using Flatten

julia> struct Foo{A,B,C}
           a::A
           b::B
           c::C
       end

julia> struct Bar{X,Y}
           x::X
           y::Y
       end

julia> parenttypeflatten(Foo(1, 2, Bar(3, 4)))
(Foo{Int64,Int64,Bar{Int64,Int64}}, Foo{Int64,Int64,Bar{Int64,Int64}}, Bar{Int64,Int64}, Bar{Int64,Int64})
```
