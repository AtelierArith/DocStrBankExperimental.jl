`dominates(λ,μ)`

The  dominance  order  on  partitions  is  an  important  partial  order in representation theory. `λ` dominates `μ` if and only if for all `i` we have `sum(λ[1:i])≥sum(μ[1:i])`.

```julia-repl
julia> dominates([5,4],[4,4,1])
true
```
