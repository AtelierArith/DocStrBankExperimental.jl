```
knotaverages(basis::BSplineBasis; indices=eachindex(basis))
```

Return the knot averages `τ[i] = mean(knots[i+1:i+order-1])` for `i ∈ indices` and the knots and order of `basis`. The knot averages are recommended in [^deBoor1978] (p. 214) as data points for interpolation.

See also: [`knotaverages!`](@ref)

[^deBoor1978]: Carl de Boor, *A Practical Guide to Splines*, New York, N.Y.: Springer, 1978.

# Examples

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
