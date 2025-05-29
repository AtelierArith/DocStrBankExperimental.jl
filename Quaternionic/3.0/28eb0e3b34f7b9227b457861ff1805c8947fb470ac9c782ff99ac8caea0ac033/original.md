```
Rotor{T<:Number} <: Number
```

Quaternion of unit magnitude with elements of type `T`.  These objects can be significantly faster *and* more accurate in certain operations representing rotations.

A rotor is typically considered to be an element of the group $\mathrm{Spin}(3) ≃ \mathrm{SU}(2)$, which can be thought of as the subgroup of quaternions with norm 1.  They are particularly useful as representations of rotations because a rotor $R$ acts on a vector $\vec{v}$ by "conjugation" as

$$
\vec{v}' = R\, \vec{v}\, R^{-1}.
$$

(which can be represented in code as `R * v / R` or, more efficiently, as `R(v)`).  This operation preserves the inner product between any two vectors conjugated in this way, and so is a rotation.  Note that, because there are two factors of $R$ here, the sign of $R$ does not affect the result.  Therefore, $\mathrm{Spin}(3)$ forms a *double* cover of the rotation group $\mathrm{SO}(3)$.  For this reason, it will occasionally be useful to disregard or arbitrarily change the sign of a `Rotor` (as in [`distance`](@ref) functions) — though this is not generally the default, and may cause problems if the input rotors change sign when the corresponding rotations are not so different (cf. [`unflip`](@ref)).

`RotorF16`, `RotorF32` and `RotorF64` are aliases for `Rotor{Float16}`, `Rotor{Float32}` and `Rotor{Float64}` respectively.  See also [`Quaternion`](@ref) and [`QuatVec`](@ref).

The functions

```
rotor(w, x, y, z)
rotor(w)
```

create a new rotor with the given components (where the components are as described in [`Quaternion`](@ref)), automatically normalizing them on input.  Note that this normalization step is the key difference between the `Rotor` and `rotor` functions; if you would like to bypass normalization, you can call

```
Rotor{T}(w, x, y, z)
Rotor{T}(w)
```

in the same way as `rotor`, and `w, x, y, z` will be converted to type `T`.  Alternatively, you can call

```
Rotor{T}(v)
```

where `v<:AbstractArray` can be converted to an `SVector{4, T}`.  If you want to handle the normalization step, you can use [`normalize`](@ref).

However, once a `Rotor` is created, its norm will often be *assumed* to be precisely 1.  So if its true norm is significantly different, you will likely see weird results — including vectors with very different lengths after "rotation" by a non-unit `Rotor`.

Note that simply creating a `Quaternion` that happens to have norm 1 does not make it a `Rotor`.  However, you can pass such a `Quaternion` to the `rotor` function and get the desired result.

# Examples

```jldoctest
julia> rotor(1, 2, 3, 4)
rotor(0.18257418583505536 + 0.3651483716701107𝐢 + 0.5477225575051661𝐣 + 0.7302967433402214𝐤)
julia> rotor(quaternion(1, 2, 3, 4))
rotor(0.18257418583505536 + 0.3651483716701107𝐢 + 0.5477225575051661𝐣 + 0.7302967433402214𝐤)
julia> Rotor{Float16}(1, 2, 3, 4)
rotor(1.0 + 2.0𝐢 + 3.0𝐣 + 4.0𝐤)
julia> normalize(Rotor{Float16}(1, 2, 3, 4))
rotor(0.1826 + 0.3652𝐢 + 0.548𝐣 + 0.7305𝐤)
julia> rotor(1.0)
rotor(1.0 + 0.0𝐢 + 0.0𝐣 + 0.0𝐤)
```
