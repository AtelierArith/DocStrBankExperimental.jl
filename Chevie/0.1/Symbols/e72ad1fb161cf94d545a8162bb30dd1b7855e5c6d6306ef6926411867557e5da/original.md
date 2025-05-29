`stringsymbol(io=stdout,S)` string for symbol `S` [taking `io` in account].

```julia-repl
julia> stringsymbol.(rio(),symbols(3,3,0))
12-element Vector{String}:
 "(1+)"
 "(1ζ₃)"
 "(1ζ₃²)"
 "(01,12,02)"
 "(01,02,12)"
 "(012,012,123)"
 "(0,1,2)"
 "(0,2,1)"
 "(01,01,13)"
 "(0,0,3)"
 "(012,,)"
 "(012,012,)"
```
