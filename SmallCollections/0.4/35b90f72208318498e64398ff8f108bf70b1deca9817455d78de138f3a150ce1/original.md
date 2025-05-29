```
SmallVector{N,T} <: AbstractSmallVector{N,T}

SmallVector{N,T}()
SmallVector{N,T}(iter)
SmallVector{N}(iter)
SmallVector(v::PackedVector{T})
SmallVector(v::AbstractSmallVector)
```

`SmallVector{N,T}` is an immutable vector type that can hold up to `N` elements of type `T`. Here `N` can be any (small) positive integer. However, at least for bit integer and hardware float types, one usually takes `N` to be a power of `2`.

The element type `T` can be omitted when creating the `SmallVector` from an iterator that has an element type, for example from an `AbstractVector` or a tuple. In the latter case, `T` is determined by promoting the element types of the tuple. If no argument is given, then an empty vector is returned. If the `SmallVector` is created from an `AbstractSmallVector` or `PackedVector` `v` and the parameter `N` is omitted, then it is set to capacity of `v`.

The unused elements of a `SmallVector{N,T}` are filled with the value `default(T)`, which is predefined for several types including `Number`. Default values for other types must be defined explicitly.

Addition and subtraction of two `SmallVector`s is possible even if the vectors have different capacity. (Of course, their lengths must agree.) The capacity of the result is the smaller of the arguments' capacities in this case.

See also [`MutableSmallVector`](@ref), [`capacity`](@ref), [`SmallCollections.default`](@ref), `Base.IteratorEltype`, `promote_type`.

# Examples

```jldoctest
julia> v = SmallVector{8,Int8}(2*x for x in 1:3)
3-element SmallVector{8, Int8}:
 2
 4
 6

julia> w = SmallVector{9}((1, 2.5, 4))
3-element SmallVector{9, Float64}:
 1.0
 2.5
 4.0

julia> v+w
3-element SmallVector{8, Float64}:
  3.0
  6.5
 10.0
```
