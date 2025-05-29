```
scale(tns, delta...)
```

Create a `ScaleArray` such that `scale(tns, delta...)[i...] == tns[i .* delta...]`.  The dimensions declared by an OffsetArray are shifted, so that `size(scale(tns, delta...)) == size(tns) .* delta`.  This is only supported on tensors with real-valued dimensions.
