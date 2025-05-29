```
quat(w, [x, y, z])
```

Convert real numbers or arrays to quaternion. `x, y, z` defaults to zero.

# Examples

```jldoctest
julia> quat(7)
Quaternion{Int64}(7, 0, 0, 0)

julia> quat(1.0, 2, 3, 4)
QuaternionF64(1.0, 2.0, 3.0, 4.0)

julia> quat([1, 2, 3])
3-element Vector{Quaternion{Int64}}:
 Quaternion{Int64}(1, 0, 0, 0)
 Quaternion{Int64}(2, 0, 0, 0)
 Quaternion{Int64}(3, 0, 0, 0)
```
