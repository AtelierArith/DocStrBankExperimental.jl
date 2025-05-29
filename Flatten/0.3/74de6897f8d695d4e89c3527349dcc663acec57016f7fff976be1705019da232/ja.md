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
