```
UpperTriangular(S::AbstractVector, n::Int)
```

ベクトルから上三角行列を構築します。

上三角行列は、対角線と下三角にゼロがある $n\times{}n$ 行列です。

データは、他の行列と同様にベクトル $S$ に格納されます。[`LowerTriangular`](@ref)、[`SkewSymMatrix`](@ref)、および [`SymmetricMatrix`](@ref) を参照してください。

構造体には2つのフィールドがあります：`S` と `n`。最初のフィールドは、行列のすべてのエントリをスパースな形式（ベクトル内）で格納し、2番目は $A\in\mathbb{R}^{n\times{}n}$ の次元 $n$ です。

# 例

```jldoctest
using GeometricMachineLearning
S = [1, 2, 3, 4, 5, 6]
UpperTriangular(S, 4)

# 出力

4×4 UpperTriangular{Int64, Vector{Int64}}:
 0  1  2  4
 0  0  3  5
 0  0  0  6
 0  0  0  0
```
