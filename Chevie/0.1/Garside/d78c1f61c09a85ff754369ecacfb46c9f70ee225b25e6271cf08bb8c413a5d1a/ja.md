`rightlcm(a₁,…,aₙ)` `rightlcmc(a₁,…,aₙ)`

`a₁,…,aₙ` は同じガーサイドモノイドの要素である必要があります。この関数は `a₁,…,aₙ` の最小共通右倍数 `m` を返します。

`rightlcmc` は '(m,(a₁⁻¹*m,…,aₙ⁻¹*m))' を返します。

```julia-repl
julia> B=BraidMonoid(coxgroup(:A,3))
BraidMonoid(A₃)

julia> rightlcmc(B(2,1,2)^2,B(3,2)^2)
(Δ², (321.123, 12321.321))
```
