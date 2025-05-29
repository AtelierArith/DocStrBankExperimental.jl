```
opposite(a::AbstractLinear{T,R}) -> Linear
```

Apply `opposite` to the terms in `a` and return a linear combination of them. If the degree of a term `x` is congruent to `1` or `2` mod `4`, then it is transformed to `-opposite(x)` and otherwise to `opposite(x)`.

Note that this function is **not** the linear extension of `opposite(x::AbstractSimplex)` or `OppositeSimplex`. The signs are chosen such that this function is a chain map from the chain complex of the simplicial set containing the terms `x` to the opposite simplicial set.

See also [`opposite(::AbstractSimplex)`](@ref), [`opposite(::AbstractTensor)`](@ref).

# Examples

```jldoctest
julia> using LinearCombinations; using LinearCombinations: diff

julia> a = Linear(SymbolicSimplex(:x, 1) => 2)
Linear{SymbolicSimplex{Symbol}, Int64} with 1 term:
2*x[0,1]

julia> b = opposite(a)
Linear{OppositeSimplex{SymbolicSimplex{Symbol}}, Int64} with 1 term:
-2*OppositeSimplex(x[0,1])

julia> diff(b) == opposite(diff(a))
true

julia> c = Linear(OppositeSimplex(y) => c for (y, c) in a)
Linear{OppositeSimplex{SymbolicSimplex{Symbol}}, Int64} with 1 term:
2*OppositeSimplex(x[0,1])

julia> diff(c) == opposite(diff(a))
false
```
