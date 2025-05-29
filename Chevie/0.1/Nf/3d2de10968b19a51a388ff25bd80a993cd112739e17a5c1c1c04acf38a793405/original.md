`NF(gens...)` or `NF(gens::AbstractVector)`

returns the smallest number field containing the elements `gens`, which may be `Cyc`, `Root1`, `Integer` or `Rational{<:Integer}`.

```julia-repl
julia> NF(E(3),root(5))
NF(15,4₁₅)

julia> NF([E(3),root(5)])
NF(15,4₁₅)
```
