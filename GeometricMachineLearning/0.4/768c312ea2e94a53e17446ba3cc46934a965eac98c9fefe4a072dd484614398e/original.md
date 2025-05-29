```
UpperTriangular(A::AbstractMatrix)
```

Build an upper-triangular matrix from a matrix.

This is done by taking the upper right of that matrix.

# Examples

```jldoctest
using GeometricMachineLearning
M = [1 2 3 4; 5 6 7 8; 9 10 11 12; 13 14 15 16]
UpperTriangular(M)

# output

4×4 UpperTriangular{Int64, Vector{Int64}}:
 0  2  3   4
 0  0  7   8
 0  0  0  12
 0  0  0   0
```
