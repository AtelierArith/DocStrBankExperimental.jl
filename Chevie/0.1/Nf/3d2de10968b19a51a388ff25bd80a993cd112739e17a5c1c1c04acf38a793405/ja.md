`NF(gens...)` または `NF(gens::AbstractVector)`

は、要素 `gens` を含む最小の数体を返します。`gens` は `Cyc`、`Root1`、`Integer` または `Rational{<:Integer}` である可能性があります。

```julia-repl
julia> NF(E(3),root(5))
NF(15,4₁₅)

julia> NF([E(3),root(5)])
NF(15,4₁₅)
```
