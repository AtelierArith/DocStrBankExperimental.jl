`subs(p::CycPol,v::Pol)`

`CycPol(p(v))`を計算するための高速ルーチンですが、次の2種類の多項式にのみ対応しています：

  * `v=Pol([e],1)` で `e` は `Root1`、すなわち `e=ζₙᵏ` のときの値
  * `v=Pol([1],n)` で `qⁿ` のときの値

```julia-repl
julia> p=CycPol(Pol()^2-1)
Φ₁Φ₂

julia> subs(p,Pol([E(3)],1))
ζ₃²Φ″₃Φ′₆

julia> subs(p,Pol()^2)
Φ₁Φ₂Φ₄
```
