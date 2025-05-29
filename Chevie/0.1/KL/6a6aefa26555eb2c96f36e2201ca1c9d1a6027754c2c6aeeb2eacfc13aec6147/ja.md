`LeftCell(W,w)`

は、要素 `w` を含む `hecke(W,q)` のための `W` の左セルを記述するレコードを返します。

```julia-repl
julia> W=coxgroup(:E,8)
E₈

julia> LeftCell(W,W((1:8)...))
LeftCell<E₈: duflo=(42,43) character=φ₃₅‚₂>
```
