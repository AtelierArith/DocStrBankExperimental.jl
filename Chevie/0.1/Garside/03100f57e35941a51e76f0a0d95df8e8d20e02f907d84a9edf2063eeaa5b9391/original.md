`word(M::GarsideMonoid,w)`

returns a word in the atoms of `M` representing the simple `w`

```julia-repl
julia> B=BraidMonoid(coxgroup(:A,3))
BraidMonoid(A₃)

julia> word(B,B.δ)
6-element Vector{Int64}:
 1
 2
 1
 3
 2
 1
```
