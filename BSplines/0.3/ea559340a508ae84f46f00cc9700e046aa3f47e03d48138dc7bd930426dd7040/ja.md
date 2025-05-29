```
knotaverages(basis::BSplineBasis; indices=eachindex(basis))
```

返されるノット平均 `τ[i] = mean(knots[i+1:i+order-1])` は `i ∈ indices` と `basis` のノットとオーダーに基づいています。ノット平均は補間のデータポイントとして [^deBoor1978] (p. 214) で推奨されています。

参照: [`knotaverages!`](@ref)

[^deBoor1978]: Carl de Boor, *A Practical Guide to Splines*, New York, N.Y.: Springer, 1978.

# 例

```jldoctest
julia> knotaverages(BSplineBasis(3, 0:5))
7-element Vector{Float64}:
 0.0
 0.5
 1.5
 2.5
 3.5
 4.5
 5.0

julia> knotaverages(BSplineBasis(4, [1, 3//2, 5//2, 4]), indices=2:6)
5-element Vector{Rational{Int64}}:
 7//6
 5//3
 8//3
 7//2
 4//1
```
