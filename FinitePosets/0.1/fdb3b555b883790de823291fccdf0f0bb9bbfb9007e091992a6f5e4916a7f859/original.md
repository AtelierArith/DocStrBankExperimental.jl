`nlinear_extensions(P;lim=10^7)`  where  `P`  is  a  `Poset`  or a `CPoset` returns  the number of linear extensions of  `P`. It gives an error if this number  is `>lim` (the default of 10^7 is attained in a few seconds).

```julia-repl
julia> nlinear_extensions(CPoset(:antichain,10))
3628800
```
