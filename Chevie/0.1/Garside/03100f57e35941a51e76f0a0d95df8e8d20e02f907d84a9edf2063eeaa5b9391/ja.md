`word(M::GarsideMonoid,w)`

は、単純な `w` を表す `M` の原子の単語を返します。

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
