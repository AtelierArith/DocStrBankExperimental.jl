```
PackedVector{U<:Unsigned,M,T<:Union{Base.BitInteger,Bool}} <: AbstractCapacityVector{T}

PackedVector{U,M,T}()
PackedVector{U,M,T}(iter)
PackedVector{U,M}(v::AbstractVector{T})
PackedVector{U,M}(t::Tuple)
PackedVector(v::AbstractSmallVector{M,T})
```

This type of immutable vector stores the elements in a common bit mask of type `U` with `M` bits for each entry. The range of allowed values is `-2^(M-1):2^(M-1)-1` if `T <: Signed`, `0:2^M-1` if `T <: Unsigned` and `false:true` if `T == Bool`. Apart from that, the official element type `T` is only used when retrieving an entry.  The capacity, that is, the number of elements that can be stored, is given by `bitsize(U)÷M`.

The element type `T` can be omitted when creating the `PackedVector` from an `AbstractVector` or from a tuple. In the latter case, `T` is determined by promoting the element types of the tuple. If no argument is given, then an empty vector is returned. If the `PackedVector` is created from a `AbstractSmallVector` `v` and the parameters `U` and `M` are omitted, then `M` is set to `bitsize(T)` and `U` is chosen such that the capacity of the resulting vector is at least the capacity of `v`.

Overflow or underflow during addition or subtraction of vectors do not throw an error. The same applies to multiplication by a scalar of type `T`. Scalar multiplication by other types returns a `Vector`.

Compared to a `SmallVector`, a `PackedVector` may have faster insert and delete operations. Arithmetic operations are usually slower unless `M` is the size of a hardware integer.

See also [`capacity`](@ref capacity(::Type{<:PackedVector})), [`SmallCollections.bitsize`](@ref).

# Examples

```jldoctest
julia> v = PackedVector{UInt64,5,Int8}(-5:5:10)
4-element PackedVector{UInt64, 5, Int8}:
 -5
  0
  5
 10

julia> capacity(v)
12

julia> w = PackedVector{UInt64,5,Int8}([1, 2, 3, 4])
4-element PackedVector{UInt64, 5, Int8}:
 1
 2
 3
 4

julia> v+w
4-element PackedVector{UInt64, 5, Int8}:
 -4
  2
  8
 14

julia> Int8(2)*v
4-element PackedVector{UInt64, 5, Int8}:
 -10
   0
  10
 -12
```
