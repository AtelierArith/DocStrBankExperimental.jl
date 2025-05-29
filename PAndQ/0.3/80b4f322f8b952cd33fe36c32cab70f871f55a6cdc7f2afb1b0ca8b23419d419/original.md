```
solutions(p)
```

Return a stateful iterator of [`valuations`](@ref) such that `interpret(valuation, p) == ⊤`.

To find every valuation that results in a true interpretation, convert the proposition to conjunctive normal form using [`normalize`](@ref). Otherwise, a subset of those valuations will be identified using the [`tseytin`](@ref) transformation.

See also [`interpret`](@ref) and [`tautology`](@ref).

# Examples

```jldoctest
julia> map(collect, solutions(⊤))
1-element Vector{Vector{Any}}:
 []

julia> @atomize map(collect, solutions(p))
1-element Vector{Vector{Pair{PAndQ.Variable, Bool}}}:
 [PAndQ.Variable(:p) => 1]

julia> map(collect, solutions(⊥))
Any[]
```
