```
PoolDims(x_size::NTuple{M}, k::Union{NTuple{L, Int}, Int};
         stride=k, padding=0, dilation=1)  where {M, L}
```

Dimensions for a "pooling" operation that can have an arbitrary input size, kernel size, stride, dilation, and channel count.  Used to dispatch onto efficient implementations at compile-time.
