```
fusiontrees(uncoupled::NTuple{N,I}[,
    coupled::I=one(I)[, isdual::NTuple{N,Bool}=ntuple(n -> false, length(uncoupled))]])
    where {N,I<:Sector} -> FusionTreeIterator{I,N,I}
```

与えられた結合されたセクターラベル `coupled` と非結合セクターラベルおよび同型 `uncoupled` と `isdual` に対して、すべての融合木を返すイテレーターを返します。
