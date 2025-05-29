left_divisors(M::LocallyGarsideMonoid, s)

left_divisors(M::LocallyGarsideMonoid, s,i)

all  the left-divisors  of the  simple element  `s` of  `M`, as a vector of vectors   of  simples,  where  the  i+1-th  vector  of  simples  holds  the left-divisors  of length i in the atoms.  If a third argument `i` is given, returns the list of divisors of length `i`.

```julia-repl
julia> W=coxgroup(:A,3)
A₃

julia> B=BraidMonoid(W)
BraidMonoid(A₃)

julia> map(x->B.(x),left_divisors(B,W(1,3,2)))
4-element Vector{Vector{GarsideElt{Perm{Int16}, BraidMonoid{Perm{Int16}, FiniteCoxeterGroup{Perm{Int16},Int64}}}}}:
 [.]
 [1, 3]
 [13]
 [132]

julia> B=DualBraidMonoid(W)
DualBraidMonoid(A₃,c=[1, 3, 2])

julia> map(x->B.(x),left_divisors(B,W(1,3,2)))
4-element Vector{Vector{GarsideElt{Perm{Int16}, DualBraidMonoid{Perm{Int16}, FiniteCoxeterGroup{Perm{Int16},Int64}}}}}:
 [.]
 [1, 2, 3, 4, 5, 6]
 [12, 13, 15, 25, 34, 45]
 [δ]
```
