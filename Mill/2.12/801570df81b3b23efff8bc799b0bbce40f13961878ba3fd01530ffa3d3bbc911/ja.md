```
PostImputingMatrix(W::AbstractMatrix{T}, ψ=zeros(T, size(W, 1))) where T
```

`W`とデフォルトパラメータ`ψ`を持つ[`PostImputingMatrix`](@ref)を構築します。

# 例

```jldoctest
julia> PostImputingMatrix([1 2; 3 4])
2×2 PostImputingMatrix{Int64, Matrix{Int64}, Vector{Int64}}:
W:
 1  2
 3  4

ψ:
 0
 0
```

関連項目: [`PreImputingMatrix`](@ref).
