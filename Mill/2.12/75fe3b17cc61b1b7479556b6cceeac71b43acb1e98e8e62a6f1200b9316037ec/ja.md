```
PreImputingMatrix(W::AbstractMatrix{T}, ψ=zeros(T, size(W, 2))) where T
```

`W` とデフォルトパラメータ `ψ` を持つ [`PreImputingMatrix`](@ref) を構築します。

# 例

```jldoctest
julia> PreImputingMatrix([1 2; 3 4])
2×2 PreImputingMatrix{Int64, Matrix{Int64}, Vector{Int64}}:
W:
 1  2
 3  4

ψ:
 0  0
```

関連情報: [`PostImputingMatrix`](@ref).
