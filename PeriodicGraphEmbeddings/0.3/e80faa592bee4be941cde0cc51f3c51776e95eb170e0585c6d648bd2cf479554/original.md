```
(pd2::PeriodicDistance2)(x, y=nothing, ofsx=nothing, ofsy=nothing; fromcartesian=false, ofs=nothing)
```

Squared periodic distance between points `x` and `y`, optionally with respective offsets `ofsx` and `ofsy`. The periodic distance is the shortest distance between all the periodic images of the inputs. For `x` and `y` given as triplets of fractional coordinates, putting integer offsets in `ofsx` and `ofsy` does not have any effect thus.

If `y` is not set, compute the periodic distance between `x` and the origin.

If `fromcartesian` is set, the inputs must be given as cartesian coordinates. Otherwise, it is assumed that the input is given in fractional coordinates.

If `ofs` is set to a mutable vector of integers (`MVector{3,Int}` from StaticArrays.jl is suggested), then the offset of the translation of `y .+ ofsy` with respect to `x .+ ofsx` is stored in `ofs`. This means that the returned periodic distance is equal to the non-periodic distance between `y .+ ofsy .+ ofs` and `x .+ ofsx` (assuming fractional coordinates). The offset is always returned as a triplet of integers, though the input can be given in cartesian coordinates as long as `fromcartesian` is set.

!!! warning
    This function modifies an internal  state of `pd2`, and is thus not thread-safe.


## Example

```jldoctest
julia> mat = [26.04 -7.71 -8.32; 0.0 32.72 -3.38; 0.0 0.0 26.66];

julia> pd2 = PeriodicDistance2(mat)
PeriodicDistance2([26.04 -7.71 -8.32; 0.0 32.72 -3.38; 0.0 0.0 26.66])

julia> sqrt(pd2([0.5, 0, 0])) # distance to the middle of the a axis is simply a/2
13.02

julia> ofs = MVector{3,Int}(undef);

julia> vec1 = [0.9, 0.6, 0.5]; vec2 = [0.0, 0.5, 0.01];

julia> d2 = pd2(vec1, vec2; ofs)
210.57932044000003

julia> println(ofs) # the offset of vec2 to have the closest image to vec1
[1, 0, 1]

julia> norm(mat*(vec2 .+ ofs .- vec1))^2 ≈ d2
true

julia> pd2(mat*vec1, mat*vec2; fromcartesian=true) ≈ d2
true
```
