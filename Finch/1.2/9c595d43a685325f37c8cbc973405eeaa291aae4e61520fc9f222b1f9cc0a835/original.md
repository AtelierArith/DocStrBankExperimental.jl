```
offset(tns, delta...)
```

Create an `OffsetArray` such that `offset(tns, delta...)[i...] == tns[i .+ delta...]`. The dimensions declared by an OffsetArray are shifted, so that `size(offset(tns, delta...)) == size(tns) .+ delta`.
