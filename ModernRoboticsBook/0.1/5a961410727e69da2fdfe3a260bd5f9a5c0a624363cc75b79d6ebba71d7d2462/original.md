```
Adjoint(T)
```

Computes the adjoint representation of a homogeneous transformation matrix.

# Examples

```jldoctest; setup = :(using ModernRoboticsBook)
julia> Adjoint([1 0 0 0; 0 0 -1 0; 0 1 0 3; 0 0 0 1])
6×6 Matrix{Float64}:
 1.0  0.0   0.0  0.0  0.0   0.0
 0.0  0.0  -1.0  0.0  0.0   0.0
 0.0  1.0   0.0  0.0  0.0   0.0
 0.0  0.0   3.0  1.0  0.0   0.0
 3.0  0.0   0.0  0.0  0.0  -1.0
 0.0  0.0   0.0  0.0  1.0   0.0
```
