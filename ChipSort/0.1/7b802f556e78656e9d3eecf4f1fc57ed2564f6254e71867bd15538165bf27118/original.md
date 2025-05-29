```
sort_net(input::Vararg{T, L}) where {L,T}
```

Applies a sorting network of size L to the input elements, returning a sorted tuple.

The elements must support the `min` and `max` functions. In the case of `SIMD.Vec` objects each "lane" across the vectors will be sorted. Therefore with L vectors of size N this function will produce N sorted sequences of size L, after the data is transposed (see transpose_vecs).
