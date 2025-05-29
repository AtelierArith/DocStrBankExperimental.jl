`leftgcd(a₁,…,aₙ)` `leftgcdc(a₁,…,aₙ)`

`a₁,…,aₙ`  should be  elements of  the same  (locally) Garside  monoid. The function returns the left gcd `d` of `a₁,…,aₙ`.

`leftgcdc` returns `(d,(d⁻¹a₁,…,d⁻¹aₙ))`.

```julia-repl
julia> W=coxgroup(:A,3)
A₃

julia> B=BraidMonoid(W)
BraidMonoid(A₃)

julia> leftgcdc(B(2,1,2)^2,B(3,2)^2)
(2, (121.21, 32.2))
```
