```
PostImputingMatrix{T <: Number, U <: AbstractMatrix{T}, V <: AbstractVector{T}} <: AbstractMatrix{T}
```

欠損列に遭遇した際にデフォルトのパラメータベクターで埋めるパラメータ化された行列です。

[`NGramMatrix`](@ref)、[`MaybeHotMatrix`](@ref)、および[`MaybeHotVector`](@ref)との乗算をサポートします。他の`AbstractMatrix`に対しては標準の乗算にフォールバックします。

# 例

```jldoctest
julia> A = PostImputingMatrix(ones(2, 2), -ones(2))
2×2 PostImputingMatrix{Float64, Matrix{Float64}, Vector{Float64}}:
W:
 1.0  1.0
 1.0  1.0

ψ:
 -1.0
 -1.0

julia> A * maybehotbatch([1, missing], 1:2)
2×2 Matrix{Float64}:
 1.0  -1.0
 1.0  -1.0
```

関連情報: [`PreImputingMatrix`](@ref).
