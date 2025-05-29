```
get_minima_and_edgelengths(points, binning_scheme::RectangularBinning) -> (Vector{Float}, Vector{Float})
```

Find the minima along each axis of the embedding, and computes appropriate `edge_lengths` given a rectangular `binning_scheme`, which provide instructions on how to  grid the space. Assumes the input is a vector of points.

See documentation for [`RectangularBinning`](@ref) for details on the  binning scheme.
