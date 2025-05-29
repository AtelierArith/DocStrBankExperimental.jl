```
SymmetricMatrix(S::AbstractVector, n::Integer)
```

ベクトル `S` に格納された情報を使用して対称行列をインスタンス化します。

`SymmetricMatrix` $A$ は行列 $A^T = A$ です。

内部的に `struct` はサイズ $n(n+1)\div2$ のベクトル $S$ を保存します。変換は次のように行われます：

$$
[A]_{ij} = \begin{cases} S[( (i-1) i ) \div 2 + j] & \text{if $i\geq{}j$}\\ 
                         S[( (j-1) j ) \div 2 + i] & \text{else}. \end{cases}
$$

したがって、$S$ は $A$ から取られたベクトルの列を保存します：$S = [\tilde{a}_1, \tilde{a}_2, \ldots, \tilde{a}_n]$ で、$\tilde{a}_i = [[A]_{i1},[A]_{i2},\ldots,[A]_{ii}]$ です。

また、[`SkewSymMatrix`](@ref)、[`LowerTriangular`](@ref)、および [`UpperTriangular`](@ref) も参照してください。

# 例

```jldoctest
using GeometricMachineLearning
S = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
SymmetricMatrix(S, 4)

# 出力

4×4 SymmetricMatrix{Int64, Vector{Int64}}:
 1  2  4   7
 2  3  5   8
 4  5  6   9
 7  8  9  10
```
