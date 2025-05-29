```
Quaternion{T<:Number} <: Number
```

Quaternionic number type with elements of type `T`.

`QuaternionF16`, `QuaternionF32` and `QuaternionF64` are aliases for `Quaternion{Float16}`, `Quaternion{Float32}` and `Quaternion{Float64}` respectively.  See also [`Rotor`](@ref) and [`QuatVec`](@ref).

The functions

```
quaternion(w, x, y, z)
quaternion(x, y, z)
quaternion(w)
```

create a new quaternion with the given components.  The argument `w` is the scalar component, and `x`, `y`, and `z` are the corresponding "vector" components.  If any of these arguments is missing, it will be set to zero.  The type of the returned quaternion will be inferred from the input arguments, or can be specified, by passing the type parameter `T` as above.

Note that the constants [`imx`](@ref), [`imy`](@ref), and [`imz`](@ref) can also be used like the complex `im` to create new `Quaternion` object.

# Examples

```jldoctest
julia> quaternion(1, 2, 3, 4)
1 + 2𝐢 + 3𝐣 + 4𝐤
julia> Quaternion{Float64}(1, 2, 3, 4)
1.0 + 2.0𝐢 + 3.0𝐣 + 4.0𝐤
julia> quaternion(1.0, 2.0, 3.0, 4.0)
1.0 + 2.0𝐢 + 3.0𝐣 + 4.0𝐤
julia> quaternion(2, 3, 4)
0 + 2𝐢 + 3𝐣 + 4𝐤
julia> quaternion(1)
1 + 0𝐢 + 0𝐣 + 0𝐤
```
