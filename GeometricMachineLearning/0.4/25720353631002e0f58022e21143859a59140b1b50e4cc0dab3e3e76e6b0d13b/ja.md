```
SkewSymMatrix(A::AbstractMatrix)
```

`0.5 * (A - A')` を実行し、行列を効率的に（$n(n-1)/2$ のエントリを持つベクトルとして）格納します。

コンストラクタが行列を入力として呼び出されると、次の射影を介して反対称行列を返します：

$$
A \mapsto \frac{1}{2}(A - A^T).
$$

# 例

```jldoctest
using GeometricMachineLearning
M = [1 2 3 4; 5 6 7 8; 9 10 11 12; 13 14 15 16]
SkewSymMatrix(M)

# 出力

4×4 SkewSymMatrix{Float64, Vector{Float64}}:
 0.0  -1.5  -3.0  -4.5
 1.5   0.0  -1.5  -3.0
 3.0   1.5   0.0  -1.5
 4.5   3.0   1.5   0.0
```

# 拡張ヘルプ

コンストラクタは、行列が呼び出されたときに常に `SkewSymMatrix{<:AbstractFloat}` 型の行列を返すように設計されていることに注意してください。たとえこの行列が `AbstractMatrix{<:Integer}` 型であってもです。

ユーザーが `SkewSymMatrix{<:Integer}` 型の行列を割り当てたい場合は、次のように呼び出します：

```julia
SkewSymMatrix(::AbstractVector, n::Integer)
```

これは [`LowerTriangular`](@ref) および [`UpperTriangular`](@ref) とは異なり、そこでは射影は行われないことに注意してください。 ```
