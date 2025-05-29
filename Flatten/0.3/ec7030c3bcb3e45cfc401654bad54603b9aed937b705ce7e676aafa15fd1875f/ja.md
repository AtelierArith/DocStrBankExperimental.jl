```
parenttypeflatten(obj, args...)
```

オブジェクトの親タイプをフラット化します。引数は[`metaflatten`](@ref)に渡されます。

# 例

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
