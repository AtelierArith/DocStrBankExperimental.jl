```
RotInv(R)
```

Inverts a rotation matrix.

# Examples

```jldoctest; setup = :(using ModernRoboticsBook)
julia> RotInv([0 0 1; 1 0 0; 0 1 0])
3×3 adjoint(::Matrix{Int64}) with eltype Int64:
 0  1  0
 0  0  1
 1  0  0
```
