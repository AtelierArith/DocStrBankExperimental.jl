```
replaceinds(A::ITensor, inds1, inds2) -> ITensor

replaceinds!(A::ITensor, inds1, inds2)
```

Replace the Index `inds1[n]` with the Index `inds2[n]` in the ITensor, where `n` runs from `1` to `length(inds1) == length(inds2)`.

The indices must have the same space (i.e. the same dimension and QNs, if applicable).

The storage of the ITensor is not modified or copied (the output ITensor is a view of the input ITensor).
