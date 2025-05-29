```
PreImputingMatrix{T <: Number, U <: AbstractMatrix{T}, V <: AbstractVector{T}} <: AbstractMatrix{T}
```

デフォルトのパラメータベクターから要素を埋めるパラメータ化された行列で、乗算中に `missing` 要素が遭遇したときに使用されます。

# 例

```jldoctest
julia> A = PreImputingMatrix(ones(2, 2), -ones(2))
2×2 PreImputingMatrix{Float64, Matrix{Float64}, Vector{Float64}}:
W:
 1.0  1.0
 1.0  1.0

ψ:
 -1.0  -1.0

julia> A * [0 1; missing -1]
2×2 Matrix{Float64}:
 -1.0  0.0
 -1.0  0.0
```

関連項目: [`PreImputingMatrix`](@ref).
