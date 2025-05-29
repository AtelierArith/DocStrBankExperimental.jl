```
OppositeSimplex{T<:AbstractSimplex} <: AbstractSimplex
```

`OppositeSimplex(x)` is the 'opposite' simplex to `x` in the sense that `i`-th face operator corresponds to the `(n-i)`-th face operator for `x`, and likewise for degeneracy operators.

The functions `*`, `\`, `inv` and `one` with argument(s) of type `OppositeSimplex` work on the underlying simplices.

Note that the linear extension of `OppositeSimplex` would not be a chain map from the chain complex of the simplicial set containing the terms `x` to the opposite simplicial set. For this purpose there is the function `opposite`.

See also [`opposite`](@ref).

# Examples

```jldoctest
julia> using SimplicialSets: d, s

julia> x = SymbolicSimplex(:x, 3)
x[0,1,2,3]

julia> y = OppositeSimplex(x)
OppositeSimplex(x[0,1,2,3])

julia> d(y, 1)
OppositeSimplex(x[0,1,3])

julia> s(y, 1)
OppositeSimplex(x[0,1,2,2,3])

julia> z = OppositeSimplex(LoopGroupSimplex(x))
OppositeSimplex(⟨x[0,1,2,3]⟩)

julia> inv(z)
OppositeSimplex(⟨x[0,1,2,3]⁻¹⟩)
```
