```
nj(D::DataFrame; force_nonnegative_edges::Bool=false)
```

Construct a tree from a distance matrix by neighbor joining, where `D` is a `DataFrame` of the distance matrix, with taxon names taken from the header of the data frame. The rows are assumed to correspond to tips in the tree in the same order as they do in columns. With `force_nonnegative_edges` being `true`, any negative edge length is changed to 0.0 (with a message).

For the algorithm, see [Satou & Nei 1987](https://doi.org/10.1093/oxfordjournals.molbev.a040454).

See [`nj!`](@ref) for using a matrix as input.
