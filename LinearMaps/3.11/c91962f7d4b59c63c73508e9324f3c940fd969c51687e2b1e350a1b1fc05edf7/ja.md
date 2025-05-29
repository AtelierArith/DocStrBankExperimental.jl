```
mul!(Y::AbstractMatrix, A::LinearMap, b::Number) -> Y
```

線形写像 `A` の行列表現を `b` でスケーリングし、その結果を `Y` に格納して、既存の `Y` の値を上書きします。

## 例

```jldoctest; setup=(using LinearAlgebra, LinearMaps)
julia> A = LinearMap{Int}(cumsum, 3); b = 2; Y = Matrix{Int}(undef, (3,3));

julia> mul!(Y, A, b)
3×3 Matrix{Int64}:
 2  0  0
 2  2  0
 2  2  2
```
