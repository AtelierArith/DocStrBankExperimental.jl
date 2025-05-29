```
StiefelProjection(B::AbstractLieAlgHorMatrix)
```

`B` から必要な情報を抽出し、`StiefelProjection` のインスタンスを構築します。

ここで必要な情報とは、バックエンド、データ型、および行列のサイズを指します。

サイズは `B.N` と `B.n` を通じて照会されます。

# 例

```jldoctest
using GeometricMachineLearning

B₁ = rand(StiefelLieAlgHorMatrix, 5, 2)
B₂ = rand(GrassmannLieAlgHorMatrix, 5, 2)
E = [1. 0.; 0. 1.; 0. 0.; 0. 0.; 0. 0.]

StiefelProjection(B₁) ≈ StiefelProjection(B₂) ≈ E 

# 出力

true
```
