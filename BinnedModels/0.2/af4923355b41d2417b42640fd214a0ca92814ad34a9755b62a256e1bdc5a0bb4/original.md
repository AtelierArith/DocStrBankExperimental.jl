```
fit_binedges(data::AbstractVector{<:Real})::BinEdges
fit_binedges(data::NTuple{N,AbstractVector{<:Real}})::NTuple{N,BinEdges}
```

Return suitable bin edges for `data`, using `algorithm`.

`data` may be a real-valued vector, or a tuple of real-valued vectors for multi-dimensional data.
