'bell(n)'

ベル数は `bell(0)=1` で定義され、$bell(n+1)=∑_{k=0}^n {n \choose  k}bell(k)$、または `bell(n)/n!` が形式的級数 `e^(eˣ-1)` における $xⁿ$ の係数であるという事実によって定義されます。

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
