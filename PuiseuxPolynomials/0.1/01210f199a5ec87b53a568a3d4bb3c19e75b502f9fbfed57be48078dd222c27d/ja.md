`Pol(p::Mvp,v::Symbol)`

は、`Mvp` `p` の係数を変数 `v` に関して持つ多項式を返します（`Mvp` として）。変数 `v` は `p` の中で整数の冪のみで現れるべきです。

```julia-repl
julia> p=(x+y^(1//2))^3
Mvp{Int64,Rational{Int64}}: x³+3x²y½+3xy+y³⁄₂

julia> Pol(:q); Pol(p,:x)
Pol{Mvp{Int64, Rational{Int64}}}: q³+3y½q²+3yq+y³⁄₂
```

これは、例えば多項式の一つの変数に関する判別式を計算するために使用できます：

```julia-repl
julia> p=x+y^2+x^3+y^3
Mvp{Int64}: x³+x+y³+y²

julia> discriminant(Pol(p,:x))
Mvp{Int64}: 27y⁶+54y⁵+27y⁴+4
```
