```
MatrixLog6(T)
```

Computes the matrix logarithm of a homogeneous transformation matrix.

# Examples

```jldoctest; setup = :(using ModernRoboticsBook)
julia> MatrixLog6([1 0 0 0; 0 0 -1 0; 0 1 0 3; 0 0 0 1])
4×4 Matrix{Float64}:
 0.0  0.0      0.0     0.0    
 0.0  0.0     -1.5708  2.35619
 0.0  1.5708   0.0     2.35619
 0.0  0.0      0.0     0.0    
```
