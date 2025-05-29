```
Wmerge, Hmerge, mergeseq = colmerge2to1pq(W::AbstractArray, H::AbstractArray, n::Integer)
```

Merge components in `W` and `H` (columns in `W` and rows in `H`) until only `n` components remain.

`Wmerge` and `Hmerge` are the merged results with `n` components.

`mergeseq` is the sequence of merge pair ids (id1, id2). Values larger than the number of columns in `W` indicate the output of previous merge steps.
