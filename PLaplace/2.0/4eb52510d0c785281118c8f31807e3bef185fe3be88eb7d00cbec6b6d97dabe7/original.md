```julia
hasresult(data::PLaplace.PLaplaceData) -> Bool

```

Returns if the object contains a result, i.e. if an algorithm ran and converged. Should be called before the result is used via `data.v`.
