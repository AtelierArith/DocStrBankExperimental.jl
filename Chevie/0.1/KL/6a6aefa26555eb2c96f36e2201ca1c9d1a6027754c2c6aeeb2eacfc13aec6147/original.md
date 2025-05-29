`LeftCell(W,w)`

returns  a  record  describing  the  left  cell  of  `W`  for  `hecke(W,q)` containing element `w`.

```julia-repl
julia> W=coxgroup(:E,8)
E₈

julia> LeftCell(W,W((1:8)...))
LeftCell<E₈: duflo=(42,43) character=φ₃₅‚₂>
```
