`rightgcd(a₁,…,aₙ)` `rightgcdc(a₁,…,aₙ)`

`a₁,…,aₙ`  should be  elements of  the same  (locally) Garside  monoid. The function returns the right gcd `d` of `a₁,…,aₙ`

`rightgcdc` returns `(d,(a₁/d,…,aₙ/d))`.

```julia-repl
julia> W=coxgroup(:A,3)
A₃

julia> B=BraidMonoid(W)
BraidMonoid(A₃)

julia> rightgcdc(B(2,1,2)^2,B(3,2)^2)
(2.2, (12.21, 23))
```
