```
    position(value::T) -> Tuple{Real, Real}
```

This function is used for the [in](@ref) method for determine the intersections between the [Boundary](@ref) objects and points.

This function is not mented to be used directly, but to be extended for the objects `T` that your [quadtree](@ref) carries.

This function **must** return an tuple of two [Real](@ref) numbers.

For example,

```julia
mutble struct MyType
    pos::Vector{Real}
    # other fields...
end

Quadtrees.position(obj::MyType) = (obj.pos[1], obj.pos[2])
```
