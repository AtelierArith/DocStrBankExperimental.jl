```
StiefelProjection(B::AbstractLieAlgHorMatrix)
```

Extract necessary information from `B` and build an instance of `StiefelProjection`. 

Necessary information here referes to the backend, the data type and the size of the matrix.

The size is queried through `B.N` and `B.n`.

# Examples

```jldoctest
using GeometricMachineLearning

B₁ = rand(StiefelLieAlgHorMatrix, 5, 2)
B₂ = rand(GrassmannLieAlgHorMatrix, 5, 2)
E = [1. 0.; 0. 1.; 0. 0.; 0. 0.; 0. 0.]

StiefelProjection(B₁) ≈ StiefelProjection(B₂) ≈ E 

# output

true
```
