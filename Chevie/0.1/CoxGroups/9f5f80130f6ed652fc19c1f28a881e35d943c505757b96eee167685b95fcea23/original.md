`coxeter_hyperoctaedral_group(n)`  or `coxhyp(n)`

The  Hyperoctaedral group (the group of all signed permutations of ±1,…,±n) as   a  Coxeter   group  of   type  `Bₙ`,   with  generators  `(1,-1)`  and `(i,i+1)(-i,-i-1)`.

```julia-repl
julia> elements(coxhyp(2))
8-element Vector{SPerm{Int8}}:
 ()
 (1,2)
 (1,-1)
 (1,2,-1,-2)
 (1,-2,-1,2)
 (2,-2)
 (1,-2)
 (1,-1)(2,-2)
```
