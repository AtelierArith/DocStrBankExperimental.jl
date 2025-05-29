```
    position(value::T) -> Tuple{Real, Real}
```

この関数は、[in](@ref) メソッドで、[Boundary](@ref) オブジェクトと点との交差点を決定するために使用されます。

この関数は直接使用することを意図していませんが、あなたの [quadtree](@ref) が保持するオブジェクト `T` に対して拡張されるべきです。

この関数は **必ず** 2つの [Real](@ref) 数のタプルを返さなければなりません。

例えば、

```julia
mutble struct MyType
    pos::Vector{Real}
    # 他のフィールド...
end

Quadtrees.position(obj::MyType) = (obj.pos[1], obj.pos[2])
```
