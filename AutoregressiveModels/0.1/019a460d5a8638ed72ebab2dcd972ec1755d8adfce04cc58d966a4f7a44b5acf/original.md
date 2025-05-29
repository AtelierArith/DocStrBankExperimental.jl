```
bootstrap!(stats, r::VectorAutoregression; kwargs...)
```

Conduct autoregressive bootstrap for statistics specified with `stats` while assuming the data generating process can be approximated by an estimated vector autoregressive model `r`.

Each statistic to be computed needs to be paired with an array for storing the output. The number of bootstrap iterations is determined by the last dimension of the array; while the other dimensions should match the size of the statistic. For example, if the statistic is a scalar, the output array should be a vector; it should be a matrix if the statistic is a vector. The statistic is specified as a function accepting a `NamedTuple` as the single argument, which contains a field `out` that points to a view of the array indexed by the last dimension, a field `data` that provides the current sample of bootstrap data, and a field `r` for the results of VAR estimation based on `data` if the keyword `estimatevar` is `true` (`nothing` otherwise). The provided function is called in each bootstrap iteration with such a `NamedTuple` containing the updated values and the computed statistics are expected to be saved in-place to `out`. For the sake of performance, unnecessary allocations should be avoided when defining such a function. The argument `stats` can be either a `Pair` of the pre-allocated output array and the statistic function or an iterable of `Pairs` if more than one statistic is needed for the same bootstrap procedure.

# Keywords

  * `initialindex::Union{Function,Integer}=randomindex`: the row index of a data columns from `r` for selecting the initial lags to be used for the bootstrap data.
  * `drawresid::Function=wilddraw!`: a function that specifies how residuals are generated for the bootstrap data given the initial lags.
  * `correctbias=false`: conduct bias correction with [`biascorrect`](@ref).
  * `estimatevar::Bool=true`: re-estimate VAR model specified in `r` with each sample of the bootstrap data.
  * `ntasks::Integer=Threads.nthreads()`: number of tasks spawned to conduct bootstrap iterations in concurrent chunks with multiple threads.
  * `keepbootdata::Bool=false`: collect and return each sample of bootstrap data generated (with possibly very large memory usage).
