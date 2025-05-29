```
straightening_sizyge(α::Vector{<:Integer}, β::Vector{<:Integer}, γ::Vector{<:Integer}, B::BracketAlgebra)
```

Return the straightening_sizyge corresponding to `α`, `β`, `γ` as an element of the bracket algebra `B`. The lenghts of the vectors have to fulfill `length(β)==d(B)+2` and `length(γ)==d(B)-length(α)`

# Examples

```jldoctest
julia> B = BracketAlgebra(6,2)
Bracket algebra over P^2 on 6 points with point ordering 1 < 2 < 3 < 4 < 5 < 6 and coefficient ring Integers.

julia> α = [1]
1-element Vector{Int64}:
 1

julia> β = [5,6,2,3]
4-element Vector{Int64}:
 5
 6
 2
 3

julia> γ = [4]
1-element Vector{Int64}:
 4

julia> straightening_sizyge(α, β, γ, B)
[2, 3, 4][1, 5, 6] + [2, 4, 5][1, 3, 6] - [2, 4, 6][1, 3, 5] - [3, 4, 5][1, 2, 6] + [3, 4, 6][1, 2, 5] + [4, 5, 6][1, 2, 3]
```
