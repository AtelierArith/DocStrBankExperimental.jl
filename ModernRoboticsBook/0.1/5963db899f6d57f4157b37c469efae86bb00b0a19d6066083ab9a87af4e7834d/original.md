```
TransInv(T)
```

Inverts a homogeneous transformation matrix.

# Examples

```jldoctest; setup = :(using ModernRoboticsBook)
julia> TransInv([1 0 0 0; 0 0 -1 0; 0 1 0 3; 0 0 0 1])
4×4 Matrix{Int64}:
 1   0  0   0
 0   0  1  -3
 0  -1  0   0
 0   0  0   1
```
