```
knotaverages!(dest, basis::BSplineBasis; indices=eachindex(basis))
```

Calculate the knot averages `τ[i] = mean(knots[i+1:i+order-1])` for `i ∈ indices` and the knots and order of `basis` and store the result in `dest`. The knot averages are recommended in [^deBoor1978] (p. 214) as data points for interpolation.

See also: [`knotaverages`](@ref)

[^deBoor1978]: Carl de Boor, *A Practical Guide to Splines*, New York, N.Y.: Springer, 1978.

# Examples

```jldoctest
julia> dest = Vector{Float64}(undef, 7);

julia> knotaverages!(dest, BSplineBasis(3, 0:5))
7-element Vector{Float64}:
 0.0
 0.5
 1.5
 2.5
 3.5
 4.5
 5.0

julia> dest = Vector{Rational{Int}}(undef, 5);

julia> knotaverages!(dest, BSplineBasis(3, 0:5), indices=2:6)
5-element Vector{Rational{Int64}}:
 1//2
 3//2
 5//2
 7//2
 9//2
```
