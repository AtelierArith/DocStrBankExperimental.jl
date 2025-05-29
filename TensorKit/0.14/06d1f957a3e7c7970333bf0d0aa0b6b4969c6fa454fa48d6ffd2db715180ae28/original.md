```
fusiontrees(uncoupled::NTuple{N,I}[,
    coupled::I=one(I)[, isdual::NTuple{N,Bool}=ntuple(n -> false, length(uncoupled))]])
    where {N,I<:Sector} -> FusionTreeIterator{I,N,I}
```

Return an iterator over all fusion trees with a given coupled sector label `coupled` and uncoupled sector labels and isomorphisms `uncoupled` and `isdual` respectively.
