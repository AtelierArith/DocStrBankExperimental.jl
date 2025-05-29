`conjugates(c)`

returns the list of distinct galois conjugates of `c` (over the Rationals), starting with `c`

```julia-repl
julia> conjugates(1+root(5))
2-element Vector{Cyc{Int64}}:
 1+√5
 1-√5
```
