```
cost,i1,i2 = dtw(seq1, seq2, [dist=SqEuclidean, postprocess=nothing])
cost,i1,i2 = dtw(seq1, seq2, dist, i2min, i2max)
```

Perform dynamic-time warping to measure the distance between two sequences.

Find a set of indices (`i1`,`i2`) that align two series (`seq1`,`seq2`) by dynamic axis warping. Also returns the distance (after warping) according to the SemiMetric `dist`, which defaults to squared Euclidean distance (see Distances.jl). If `seq1` and `seq2` are matrices, each column is considered an observation.

If `i2min/max` are provided, do DTW to align `seq1` and `seq2` confined to a window. Vectors `i2min` and `i2max` specify (inclusive) lower and upper bounds for `seq2` for each index in `seq1`. Thus, `i2min` and `i2max` are required to be the same length as `seq1`.

If `filternernel::AbstractMatrix` is provided, it's used to filter the cost matrix. Create a suitable kerlen using, e.g., `ImageFiltering.Kernel.gaussian(3)`. The filtering of the cost matrix makes the warping smoother, effectively penalizing small-scale warping.

See also [`dtw_cost`](@ref) and [`dtwnn`](@ref).
