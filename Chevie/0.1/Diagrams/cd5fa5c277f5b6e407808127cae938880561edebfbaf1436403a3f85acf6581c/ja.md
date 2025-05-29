`diagram(W)` は、有限反射群またはスぺツ `W` のプレゼンテーションを説明する図を印刷します。

```julia-repl
julia> diagram(coxgroup(:E,8))
    O 2
    ￨
O—O—O—O—O—O—O E₈
1 3 4 5 6 7 8

julia> diagram(crg(33))
    3 ②       G₃₃
     /^\
② ——② ——② ——② 
1   2   4   5     423423=342342
```
