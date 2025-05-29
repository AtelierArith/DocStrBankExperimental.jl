```
LowerTriangular(A::AbstractMatrix)
```

Build a lower-triangular matrix from a matrix.

This is done by taking the lower left of that matrix.

# Examples

```jldoctest
using GeometricMachineLearning
M = [1 2 3 4; 5 6 7 8; 9 10 11 12; 13 14 15 16]
LowerTriangular(M)

# output

4×4 LowerTriangular{Int64, Vector{Int64}}:
  0   0   0  0
  5   0   0  0
  9  10   0  0
 13  14  15  0
```
