```
fieldtypeflatten(obj, args...)
```

オブジェクトのフィールドタイプをフラット化します。引数は[`metaflatten`](@ref)に渡されます。

# 例

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
