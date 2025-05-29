`subs(p::CycPol,v::Pol)`

a fast routine to compute `CycPol(p(v))` but works for only two types of polynomials:

  * `v=Pol([e],1)` for `e` a `Root1`, that is the value at `qe` for `e=ζₙᵏ`
  * `v=Pol([1],n)` that is the value at `qⁿ`

```julia-repl
julia> p=CycPol(Pol()^2-1)
Φ₁Φ₂

julia> subs(p,Pol([E(3)],1))
ζ₃²Φ″₃Φ′₆

julia> subs(p,Pol()^2)
Φ₁Φ₂Φ₄
```
