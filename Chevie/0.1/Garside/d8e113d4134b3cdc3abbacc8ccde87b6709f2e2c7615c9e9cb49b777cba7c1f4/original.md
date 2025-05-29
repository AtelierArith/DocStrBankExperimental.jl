`left_divisors(b::LocallyGarsideElt[, i])`

returns all left-divisors of `b` (left-divisors of length `i` if specified)

```julia-repl
julia> B=DualBraidMonoid(coxsym(4))
DualBraidMonoid(𝔖 ₄,c=[1, 3, 2])

julia> left_divisors(B(1,5,4,3))
10-element Vector{GarsideElt{Perm{Int16}, DualBraidMonoid{Perm{Int16}, CoxSym{Int16}}}}:
 .
 1
 1.4
 1.4.2
 1.4.3
 5
 6
 15
 15.4
 15.4.3

julia> left_divisors(B(1,5,4,3),1)
3-element Vector{GarsideElt{Perm{Int16}, DualBraidMonoid{Perm{Int16}, CoxSym{Int16}}}}:
 1
 5
 6
```
