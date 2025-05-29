```
function solve(
    Ψ::RegularizationProblem, 
    b::AbstractVector,
    lower::AbstractVector, 
    upper::AbstractVector;
    kwargs...
)
```

[RegularizationProblem](@ref) Ψの制約最小化、観測bおよび各xᵢの上限および下限。

この関数は、`solve(Ψ, b; kwargs...)`を使用して代数的解を計算し、上限および下限で解を切り捨て、この解を最小化問題の初期条件として使用します。返される解は、代数的解から得られた正則化パラメータλを使用しています。
