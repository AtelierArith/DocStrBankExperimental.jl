```
solve_init(A::MatElem)
```

Return a context object `C` that allows to efficiently solve linear systems $Ax = b$ or $xA = b$ for different $b$.

# Example

```jldoctest
julia> A = QQ[1 2 3; 0 3 0; 5 0 0];

julia> C = solve_init(A)
Linear solving context of matrix
  [1//1   2//1   3//1]
  [0//1   3//1   0//1]
  [5//1   0//1   0//1]

julia> solve(C, [QQ(1), QQ(1), QQ(1)]; side = :left)
3-element Vector{Rational{BigInt}}:
 1//3
 1//9
 2//15

julia> solve(C, [QQ(1), QQ(1), QQ(1)]; side = :right)
3-element Vector{Rational{BigInt}}:
 1//5
 1//3
 2//45
```
