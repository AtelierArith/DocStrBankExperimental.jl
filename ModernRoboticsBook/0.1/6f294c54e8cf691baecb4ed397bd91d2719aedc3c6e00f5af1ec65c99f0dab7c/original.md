```
MatrixExp3(so3mat)
```

Computes the matrix exponential of a matrix in so(3).

# Examples

```jldoctest; setup = :(using ModernRoboticsBook)
julia> MatrixExp3([0 -3 2; 3 0 -1; -2 1 0])
3×3 Matrix{Float64}:
 -0.694921   0.713521  0.0892929
 -0.192007  -0.303785  0.933192 
  0.692978   0.63135   0.348107 
```
