```
matrix(X; transpose=false)
```

If `X isa AbstractMatrix`, return `X` or `permutedims(X)` if `transpose=true`. Otherwise if `X` is a Tables.jl compatible table source, convert `X` into a `Matrix`.
