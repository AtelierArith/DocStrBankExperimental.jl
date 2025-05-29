`leftlcm(a₁,…,aₙ)` `leftlcmc(a₁,…,aₙ)`

`a₁,…,aₙ` は同じガーサイドモノイドの要素である必要があります。この関数は `a₁,…,aₙ` の最小共通左倍数 `m` を返します。

`leftlcmc` は '(m,(m/a₁,…,m/aₙ))' を返します。

```julia-repl
julia> B=BraidMonoid(coxgroup(:A,3))
BraidMonoid(A₃)

julia> leftlcmc(B(2,1,2)^2,B(3,2)^2)
(Δ.121, (123, 23.321))
```
