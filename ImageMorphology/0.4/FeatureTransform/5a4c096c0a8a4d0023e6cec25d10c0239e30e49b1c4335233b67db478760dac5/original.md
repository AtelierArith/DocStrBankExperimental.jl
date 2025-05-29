```
feature_transform(img::AbstractArray{Bool, N};
                  weights=nothing, nthreads=Threads.nthreads()) -> F
```

Compute the feature transform of a binary image `I`, finding the closest "feature" (positions where `I` is `true`) for each location in `I`.  Specifically, `F[i]` is a `CartesianIndex` encoding the position closest to `i` for which `I[F[i]]` is `true`.  In cases where two or more features in `I` have the same distance from `i`, an arbitrary feature is chosen. If `I` has no `true` values, then all locations are mapped to an index where each coordinate is `typemin(Int)`.

Optionally specify the weight `w` assigned to each coordinate.  For example, if `I` corresponds to an image where voxels are anisotropic, `w` could be the voxel spacing along each coordinate axis. The default value of `nothing` is equivalent to `w=(1,1,...)`.

See also: [`distance_transform`](@ref).

# Citation

  * [1] Maurer, Calvin R., Rensheng Qi, and Vijay Raghavan. "A linear time algorithm for computing exact Euclidean distance transforms of binary images in arbitrary dimensions." *IEEE Transactions on Pattern Analysis and Machine Intelligence* 25.2 (2003): 265-270.
