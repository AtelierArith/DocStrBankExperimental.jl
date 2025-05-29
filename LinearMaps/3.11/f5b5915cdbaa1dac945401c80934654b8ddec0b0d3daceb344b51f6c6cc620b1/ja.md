```
mul!(Y::AbstractMatrix, A::LinearMap, b::Number, α::Number, β::Number) -> Y
```

線形写像 `A` の行列表現を `b*α` でスケーリングし、その結果を `Y*β` に加算し、最終結果を `Y` に格納して、既存の `Y` の値を上書きします。

## 例

```jldoctest; setup=(using LinearAlgebra, LinearMaps)
julia> A = LinearMap{Int}(cumsum, 3); b = 2; Y = ones(Int, (3,3));

julia> mul!(Y, A, b, 2, 1)
3×3 Matrix{Int64}:
 5  1  1
 5  5  1
 5  5  5
```
