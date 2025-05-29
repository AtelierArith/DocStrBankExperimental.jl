```
contrast(r1::RegDIDResultOrAgg, rs::RegDIDResultOrAgg...; kwargs)
```

Construct a [`ContrastResult`](@ref) by collecting the computed least-square weights from each of the [`RegDIDResultOrAgg`](@ref).

# Keywords

  * `subset=nothing`: indices for cells to be included (rows in output).
  * `coefs=nothing`: indices for coefficients from each result to be included (columns in output).
