```
Tabloid(b::BracketAlgebraElem)
```

Return the tabloid corresponding to the bracket monomial `b`.

# Examples

```jldoctest
julia> B = BracketAlgebra(5,2)
Bracket algebra over P^2 on 5 points with point ordering 1 < 2 < 3 < 4 < 5 and coefficient ring Integers.

julia> b = B([1,2,3]) * B([1,2,5])
[1, 2, 5][1, 2, 3]

julia> Tabloid(b)
[1 2 3; 1 2 5]
```
