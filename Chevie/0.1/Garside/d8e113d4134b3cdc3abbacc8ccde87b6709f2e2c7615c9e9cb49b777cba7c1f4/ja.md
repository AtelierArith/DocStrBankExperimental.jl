`left_divisors(b::LocallyGarsideElt[, i])`

は `b` のすべての左約数を返します（指定された場合は長さ `i` の左約数）。

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
