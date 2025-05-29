```
BlockMaxima(blocksize::Int, p::Real)
```

Instructions type for [`extremevaltheory_dims_persistences`](@ref) and related functions. This method divides the input data into blocks of length `blocksize` and fits the maxima of each block to a Generalized Extreme Value distribution. In order for this method to work correctly, both the `blocksize` and the number of blocks must be high. Note that there are data points that are not used by the algorithm. Since it is not always possible to express the number of input data poins as `N = blocksize * nblocks + 1`. To reduce the number of unused data, chose an `N` equal or superior to `blocksize * nblocks + 1`. This method and several variants of it has been studied in [faranda2011numerical](@cite)

The parameter `p` is a number between 0 and 1 that determines the p-quantile for the computation of the extremal index and hence is irrelevant if `compute_persistences = false` in [`extremevaltheory_dims_persistences`](@ref).

See also [`estimate_gev_parameters`](@ref).
