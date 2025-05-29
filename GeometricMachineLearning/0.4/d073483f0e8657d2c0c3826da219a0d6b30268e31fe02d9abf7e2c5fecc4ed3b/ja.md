```
LowerTriangular(S::AbstractVector, n::Int)
```

ベクトルから下三角行列を構築します。

下三角行列は、対角線と上三角にゼロがある $n\times{}n$ 行列です。

データは、他の行列と同様にベクトル $S$ に格納されます。[`UpperTriangular`](@ref)、[`SkewSymMatrix`](@ref)、および [`SymmetricMatrix`](@ref) を参照してください。

この構造体には2つのフィールドがあります：`S` と `n`。最初のフィールドは、行列のすべてのエントリをスパースな形式（ベクトル内）で格納し、2番目は $A\in\mathbb{R}^{n\times{}n}$ の次元 $n$ です。

# 例

```jldoctest
using GeometricMachineLearning
S = [1, 2, 3, 4, 5, 6]
LowerTriangular(S, 4)

# 出力

4×4 LowerTriangular{Int64, Vector{Int64}}:
 0  0  0  0
 1  0  0  0
 2  3  0  0
 4  5  6  0
```
