`leftgcd(a₁,…,aₙ)` `leftgcdc(a₁,…,aₙ)`

`a₁,…,aₙ` は同じ（局所的に）ガルシードモノイドの要素である必要があります。この関数は `a₁,…,aₙ` の左 gcd `d` を返します。

`leftgcdc` は `(d,(d⁻¹a₁,…,d⁻¹aₙ))` を返します。

```julia-repl
julia> W=coxgroup(:A,3)
A₃

julia> B=BraidMonoid(W)
BraidMonoid(A₃)

julia> leftgcdc(B(2,1,2)^2,B(3,2)^2)
(2, (121.21, 32.2))
```
