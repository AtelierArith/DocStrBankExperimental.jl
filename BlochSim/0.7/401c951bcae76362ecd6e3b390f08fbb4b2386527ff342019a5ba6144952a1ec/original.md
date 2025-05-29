```
Magnetization(x, y, z)
Magnetization{T}()
Magnetization()
```

Create a mutable `Magnetization` object representing a 3D magnetization vector.

# Properties

  * `x::Real`: x component of magnetization vector
  * `y::Real`: y component of magnetization vector
  * `z::Real`: z component of magnetization vector

# Examples

```jldoctest
julia> M = Magnetization()
Magnetization vector with eltype Float64:
 Mx = 0.0
 My = 0.0
 Mz = 0.0

julia> M.x = 1; M.y = 2; M.z = 3; M
Magnetization vector with eltype Float64:
 Mx = 1.0
 My = 2.0
 Mz = 3.0
```
