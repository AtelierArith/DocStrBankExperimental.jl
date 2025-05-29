```
StreamSample{T}([rng], iter, n, [N], method = AlgD())
```

Initializes a stream sample, which can then be iterated over to return the sampling elements of the iterable `iter` which is assumed to have a eltype of `T`. The methods implemented in [`StreamSample`](@ref) require the knowledge of the total number of elements in the stream `N`, if not provided it is assumed to be available by calling `length(iter)`.
