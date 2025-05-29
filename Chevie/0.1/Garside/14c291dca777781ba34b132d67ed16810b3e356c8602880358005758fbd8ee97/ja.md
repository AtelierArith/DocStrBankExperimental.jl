`rightgcd(a₁,…,aₙ)` `rightgcdc(a₁,…,aₙ)`

`a₁,…,aₙ` は同じ（局所的に）ガルシードモノイドの要素である必要があります。この関数は `a₁,…,aₙ` の右gcd `d` を返します。

`rightgcdc` は `(d,(a₁/d,…,aₙ/d))` を返します。

```julia-repl
julia> W=coxgroup(:A,3)
A₃

julia> B=BraidMonoid(W)
BraidMonoid(A₃)

julia> rightgcdc(B(2,1,2)^2,B(3,2)^2)
(2.2, (12.21, 23))
```
