`rightlcm(a₁,…,aₙ)` `rightlcmc(a₁,…,aₙ)`

`a₁,…,aₙ`  should  be  elements  of  the  same Garside monoid. The function returns  the least common right multiple  `m` of `a₁,…,aₙ`.

`rightlcmc` returns '(m,(a₁⁻¹*m,…,aₙ⁻¹*m))`.

```julia-repl
julia> B=BraidMonoid(coxgroup(:A,3))
BraidMonoid(A₃)

julia> rightlcmc(B(2,1,2)^2,B(3,2)^2)
(Δ², (321.123, 12321.321))
```
