```
Wmerge, Hmerge, WHstage, Err = mergecolumns(W, H, mergeseq; tracemerge=false)
```

Merge components in `W` and `H` (columns in `W` and rows in `H`) according to the sequence of merge pair ids `mergeseq`.

`Wmerge` and `Hmerge` are the merged results.

`WHstage::Vector{Tuple{Matrix, Matrix}}` includes the results of each merge stage. `WHstage` is empty if `tracemerge=false`.

`Err::Vector` includes merge penalty of each merge stage.
