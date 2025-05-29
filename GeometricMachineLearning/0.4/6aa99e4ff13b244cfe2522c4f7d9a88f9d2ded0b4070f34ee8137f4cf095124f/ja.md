```
SymmetricMatrix(A::AbstractMatrix)
```

射影を行い、行列を効率的な方法（$n(n+1)/2$ のエントリを持つベクトルとして）で保存します。

コンストラクタが行列を入力として呼び出されると、*射影*を介して対称行列を返します：

$$
A \mapsto \frac{1}{2}(A + A^T).
$$

# 例

```jldoctest
using GeometricMachineLearning
M = [1 2 3 4; 5 6 7 8; 9 10 11 12; 13 14 15 16]
SymmetricMatrix(M)

# 出力

4×4 SymmetricMatrix{Float64, Vector{Float64}}:
 1.0   3.5   6.0   8.5
 3.5   6.0   8.5  11.0
 6.0   8.5  11.0  13.5
 8.5  11.0  13.5  16.0
```

# 拡張ヘルプ

コンストラクタは、行列が `AbstractMatrix{<:Integer}` 型であっても、常に `SymmetricMatrix{<:AbstractFloat}` 型の行列を返すように設計されています。

ユーザーが `SymmetricMatrix{<:Integer}` 型の行列を割り当てたい場合は、次のように呼び出します。

$$
julia SymmetricMatrix(::AbstractVector, n::Integer)
$$

`

これは [`LowerTriangular`](@ref) および [`UpperTriangular`](@ref) とは異なり、そこでは射影は行われません。
