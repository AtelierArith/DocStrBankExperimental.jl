```
UpperTriangular(A::AbstractMatrix)
```

行列から上三角行列を構築します。

これは、その行列の右上部分を取ることによって行われます。

# 例

```jldoctest
using GeometricMachineLearning
M = [1 2 3 4; 5 6 7 8; 9 10 11 12; 13 14 15 16]
UpperTriangular(M)

# 出力

4×4 UpperTriangular{Int64, Vector{Int64}}:
 0  2  3   4
 0  0  7   8
 0  0  0  12
 0  0  0   0
```
