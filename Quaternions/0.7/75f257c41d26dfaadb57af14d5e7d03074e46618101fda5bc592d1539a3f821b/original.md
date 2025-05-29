```
slerp(qa::Quaternion, qb::Quaternion, t::Real)
```

Spherical linear interpolation (Slerp) between the inputs `qa` and `qb`. Since the input is normalized inside the function, the absolute value of the return value will be 1.

# Examples

```jldoctest
julia> using Quaternions

julia> qa = Quaternion(1,0,0,0)
Quaternion{Int64}(1, 0, 0, 0)

julia> qb = Quaternion(0,1,0,0)
Quaternion{Int64}(0, 1, 0, 0)

julia> slerp(qa, qb, 0.6)
QuaternionF64(0.5877852522924731, 0.8090169943749475, 0.0, 0.0)

julia> ans ≈ Quaternion(cospi(0.3), sinpi(0.3), 0, 0)
true
```
