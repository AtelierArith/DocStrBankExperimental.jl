```
abstract FieldVector{N, T} <: FieldArray{Tuple{N}, 1}
```

Inheriting from this type will make it easy to create your own vector types. A `FieldVector` will automatically define `getindex` and `setindex!` appropriately. An immutable `FieldVector` will be as performant as an `SVector` of similar length and element type, while a mutable `FieldVector` will behave similarly to an `MVector`.

If you define a `FieldVector` which is parametric on the element type you should consider defining `similar_type` to preserve your array type through array operations as in the example below.

# Example

```
struct Vec3D{T} <: FieldVector{3, T}
    x::T
    y::T
    z::T
end

StaticArrays.similar_type(::Type{<:Vec3D}, ::Type{T}, s::Size{(3,)}) where {T} = Vec3D{T}
```
