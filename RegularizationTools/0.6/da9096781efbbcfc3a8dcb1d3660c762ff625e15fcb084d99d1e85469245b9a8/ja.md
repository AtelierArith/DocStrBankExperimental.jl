```
function solve(
    Ψ::RegularizationProblem, 
    b::AbstractVector,
    x₀::AbstractVector,
    lower::AbstractVector, 
    upper::AbstractVector;
    kwargs...
)
```

観測 b、初期推測 x₀、および各 xᵢ の上限と下限を持つ [RegularizationProblem](@ref) Ψ の制約最小化。

この関数は `solve(Ψ, b; kwargs...)` を使用して代数的解を計算し、上限と下限で解を切り捨て、この解を最小化問題の初期条件として使用します。返される解は、代数的解から得られた正則化パラメータ λ を使用しています。
