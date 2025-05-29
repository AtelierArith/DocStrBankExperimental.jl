'bell(n)'

The  Bell numbers are  defined by `bell(0)=1`  and $bell(n+1)=∑_{k=0}^n {n \choose  k}bell(k)$, or by the fact  that `bell(n)/n!` is the coefficient of `xⁿ` in the formal series `e^(eˣ-1)`.

```julia-repl
julia> bell.(0:6)
7-element Vector{Int64}:
   1
   1
   2
   5
  15
  52
 203

julia> bell(14)
190899322

julia> bell(big(30))
846749014511809332450147
```
