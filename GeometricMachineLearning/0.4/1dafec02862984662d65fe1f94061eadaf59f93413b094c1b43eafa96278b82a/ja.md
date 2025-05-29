```
LowerTriangular(A::AbstractMatrix)
```

行列から下三角行列を構築します。

これは、その行列の左下を取ることによって行われます。

# 例

```jldoctest
using GeometricMachineLearning
M = [1 2 3 4; 5 6 7 8; 9 10 11 12; 13 14 15 16]
LowerTriangular(M)

# 出力

4×4 LowerTriangular{Int64, Vector{Int64}}:
  0   0   0  0
  5   0   0  0
  9  10   0  0
 13  14  15  0
```
