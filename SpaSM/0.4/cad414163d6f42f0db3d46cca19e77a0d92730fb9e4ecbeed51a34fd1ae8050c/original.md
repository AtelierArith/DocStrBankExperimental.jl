```
gesv(fact::LU{F}, B::CSR{F})
```

Solve `X`*`A` == `B` where `A` has already been echelonized in `fact`.

Assumes that `fact` is a complete factorization, with `:U` and `:L` fields. Returns (X, Vector{Bool} indicating which rows of `X` are valid solutions).
