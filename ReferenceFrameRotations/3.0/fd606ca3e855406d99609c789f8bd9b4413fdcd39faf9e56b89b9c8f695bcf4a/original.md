```
Quaternion(q0::T0, q1::T1, q2::T2, q3::T3) where {T0, T1, T2, T3}
```

Create the following quaternion:

```
q0 + q1.i + q2.j + q3.k
```

in which:

  * `q0` is the real part of the quaternion.
  * `q1` is the X component of the quaternion vectorial part.
  * `q2` is the Y component of the quaternion vectorial part.
  * `q3` is the Z component of the quaternion vectorial part.

!!! note
    The quaternion type is obtained by promoting `T0`, `T1`, `T2`, and `T3`.


# Examples

```jldoctest
julia> Quaternion(1, 0, 0, 0)
Quaternion{Int64}:
  + 1 + 0⋅i + 0⋅j + 0⋅k

julia> Quaternion(1, 0, 0, 0.0)
Quaternion{Float64}:
  + 1.0 + 0.0⋅i + 0.0⋅j + 0.0⋅k
```

---

```
Quaternion(v::AbstractVector)
```

If the vector `v` has 3 components, then create a quaternion in which the real part is `0` and the vectorial or imaginary part has the same components of the vector `v`. In other words:

```
q = 0 + v[1].i + v[2].j + v[3].k
```

Otherwise, if the vector `v` has 4 components, then create a quaternion in which the elements match those of the input vector:

```
q = v[1] + v[2].i + v[3].j + v[4].k
```

!!! note
    If the length of `v` is not 3 or 4, then an error is thrown.


# Examples

```jldoctest
julia> Quaternion([0, cosd(45), sind(45)])
Quaternion{Float64}:
  + 0.0 + 0.0⋅i + 0.707107⋅j + 0.707107⋅k

julia> Quaternion([cosd(45), 0, sind(45), 0])
Quaternion{Float64}:
  + 0.707107 + 0.0⋅i + 0.707107⋅j + 0.0⋅k
```

---

```
Quaternion(r::Number, v::AbstractVector)
```

Create a quaternion with real part `r` and vectorial or imaginary part `v`:

```
r + v[1].i + v[2].j + v[3].k
```

!!! note
    The quaternion type is obtained by promoting the type of `r` and the elements of `v`.


# Examples

```jldoctest
julia> Quaternion(cosd(45), [0, sind(45), 0])
Quaternion{Float64}:
  + 0.707107 + 0.0⋅i + 0.707107⋅j + 0.0⋅k
```

---

```
Quaternion(u::UniformScaling{T}) where T
Quaternion{T}(u::UniformScaling) where T
Quaternion(u::UniformScaling, Q::Quaternion{T}) where T
```

Create the quaternion `u.λ + 0.i + 0.j + 0.k`.

If a quaternion is passed as in the third signature, then the new quaternion will have the same type.

# Examples

```jldoctest
julia> Quaternion(I)
Quaternion{Bool}:
  + true + false⋅i + false⋅j + false⋅k

julia> Quaternion(1.0I)
Quaternion{Float64}:
  + 1.0 + 0.0⋅i + 0.0⋅j + 0.0⋅k

julia> q = Quaternion{Float32}(I)
Quaternion{Float32}:
  + 1.0 + 0.0⋅i + 0.0⋅j + 0.0⋅k

julia> Quaternion(I, q)
Quaternion{Float32}:
  + 1.0 + 0.0⋅i + 0.0⋅j + 0.0⋅k
```
