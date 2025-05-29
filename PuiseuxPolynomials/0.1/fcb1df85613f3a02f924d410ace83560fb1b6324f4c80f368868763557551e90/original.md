`Mvp(p::Pol[,v])` converts `p` to  an  `Mvp`, with the same variable name   if `v` omitted or the variable name `v`.

```julia-repl
julia> @Pol q
Pol{Int64}: q

julia> Mvp(q^2+q)
Mvp{Int64}: q²+q

julia> Mvp(q^2+q,:x)
Mvp{Int64}: x²+x
```
