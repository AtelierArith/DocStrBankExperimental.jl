```
QuatVec{T<:Number} <: Number
```

Pure-vector quaternion with elements of type `T`.  These objects can be significantly faster *and* more accurate in certain operations than general `Quaternion`s.

`QuatVecF16`, `QuatVecF32` and `QuatVecF64` are aliases for `QuatVec{Float16}`, `QuatVec{Float32}` and `QuatVec{Float64}` respectively.  See also [`Quaternion`](@ref) and [`Rotor`](@ref).

The functions

```
quatvec(w, x, y, z)
quatvec(x, y, z)
quatvec(w)
```

create a new `QuatVec` with the given components (where the components are as described in [`Quaternion`](@ref)), except that the scalar argument `w` is always set to 0.

# Examples

```jldoctest
julia> quatvec(1, 2, 3, 4)
 + 2𝐢 + 3𝐣 + 4𝐤
julia> quatvec(quaternion(1, 2, 3, 4))
 + 2𝐢 + 3𝐣 + 4𝐤
julia> quatvec(2, 3, 4)
 + 2𝐢 + 3𝐣 + 4𝐤
julia> quatvec(1)
 + 0𝐢 + 0𝐣 + 0𝐤
```
