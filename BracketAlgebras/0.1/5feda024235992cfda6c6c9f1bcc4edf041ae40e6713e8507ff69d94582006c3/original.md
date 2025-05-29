```
straighten(b::BracketAlgebraElem)
```

Perform the straightening algorithm on the bracket algebra element `b` as in Stutrmfels 2008, Alg. 3.5.6. The straightening algorithm performs the groebner reduction of the bracket algebra element `b` with the straightening sizyges as a Groebner basis. The result is a normal form of `b` in which every term is standard. See also [`straightening_sizyge`](@ref), [`standard_violation`](@ref), [`is_standard`](@ref).

# Examples

```jldoctest
julia> B = BracketAlgebra(6, 2)
Bracket algebra over P^2 on 6 points with point ordering 1 < 2 < 3 < 4 < 5 < 6 and coefficient ring Integers.

julia> b = B([1,4,5])*B([1,5,6])*B([2,3,4])
[2, 3, 4][1, 5, 6][1, 4, 5]

julia> straighten(b)
[2, 5, 6][1, 4, 5][1, 3, 4] - [3, 5, 6][1, 4, 5][1, 2, 4] + [4, 5, 6][1, 4, 5][1, 2, 3]
```
