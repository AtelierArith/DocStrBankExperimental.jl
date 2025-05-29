`leftlcm(a₁,…,aₙ)` `leftlcmc(a₁,…,aₙ)`

`a₁,…,aₙ`  should  be  elements  of  the  same Garside monoid. The function returns  the least common left multiple  `m` of `a₁,…,aₙ`.

`leftlcmc` returns '(m,(m/a₁,…,m/aₙ))`.

```julia-repl
julia> B=BraidMonoid(coxgroup(:A,3))
BraidMonoid(A₃)

julia> leftlcmc(B(2,1,2)^2,B(3,2)^2)
(Δ.121, (123, 23.321))
```
