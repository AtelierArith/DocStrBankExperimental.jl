```
mul!(Y::AbstractVecOrMat, A::LinearMap, B::AbstractVector) -> Y
mul!(Y::AbstractMatrix, A::LinearMap, B::AbstractMatrix) -> Y
```

線形写像 `A` がベクトルまたは行列 `B` に作用する計算を行い、その結果を `Y` に格納します。`Y` の既存の値は上書きされます。`Y` は `A` または `B` とエイリアスされてはいけません。

## 例

```jldoctest; setup=(using LinearAlgebra, LinearMaps)
julia> A = LinearMap([1.0 2.0; 3.0 4.0]); B = ones(2); Y = similar(B); mul!(Y, A, B)
2-element Vector{Float64}:
 3.0
 7.0

julia> A = LinearMap([1.0 2.0; 3.0 4.0]); B = ones(2,2); Y = similar(B); mul!(Y, A, B)
2×2 Matrix{Float64}:
 3.0  3.0
 7.0  7.0
```
