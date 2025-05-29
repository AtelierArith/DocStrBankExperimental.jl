```
SkewSymMatrix(S::AbstractVector, n::Integer)
```

ベクトル `S` に格納された情報を使用して、斜対称行列をインスタンス化します。

斜対称行列 $A$ は、行列 $A^T = -A$ です。

内部的に `struct` はサイズ $n(n-1)\div2$ のベクトル $S$ を保存します。変換は次のように行われます：

$$
[A]_{ij} = \begin{cases} 0                             & \text{if $i=j$} \\
                         S[( (i-2) (i-1) ) \div 2 + j] & \text{if $i>j$}\\ 
                         S[( (j-2) (j-1) ) \div 2 + i] & \text{else}. \end{cases}
$$

したがって、$S$ は $A$ から取得されたベクトルの列を保存します：$S = [\tilde{a}_1, \tilde{a}_2, \ldots, \tilde{a}_n]$ で、$\tilde{a}_i = [[A]_{i1},[A]_{i2},\ldots,[A]_{i(i-1)}]$ です。

また、[`SymmetricMatrix`](@ref)、[`LowerTriangular`](@ref)、および [`UpperTriangular`](@ref) も参照してください。

# 例

```jldoctest
using GeometricMachineLearning
S = [1, 2, 3, 4, 5, 6]
SkewSymMatrix(S, 4)

# 出力

4×4 SkewSymMatrix{Int64, Vector{Int64}}:
 0  -1  -2  -4
 1   0  -3  -5
 2   3   0  -6
 4   5   6   0
```
