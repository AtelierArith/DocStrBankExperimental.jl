left_divisors(M::LocallyGarsideMonoid, s)

left_divisors(M::LocallyGarsideMonoid, s,i)

Mの単純要素`s`のすべての左約数を、単純のベクトルのベクトルとして返します。ここで、i+1番目の単純のベクトルは、原子の中で長さiの左約数を保持します。第三の引数`i`が与えられた場合、長さ`i`の約数のリストを返します。

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
