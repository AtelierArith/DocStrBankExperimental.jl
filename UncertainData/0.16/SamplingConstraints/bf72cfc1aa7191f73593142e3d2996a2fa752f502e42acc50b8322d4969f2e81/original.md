```
StrictlyIncreasing(algorithm::OrderedSamplingAlgorithm; n::Int = 50000)
```

Sampling scheme indicating element-wise sampling such that the resulting values  are strictly decreasing in magnitude. 

Decreasing sequential sampling is only guaranteed when distributions have finite support. Therefore, distributions are element-wise truncated to the lower and upper quantiles  `lq` and `uq`. For each distribution, this is done by drawing `n` values from it, then  finding the quantiles for that sample, and finally truncating the distribution to the empirical quantile range.

`algorithm` is an instance of some `OrderedSamplingAlgorithm` (e.g. `StartToEnd`). `n` is the number of samples to draw when computing quantiles. 

Typically used when there are known, physical constraints on the measurements. For example, geochemical measurements of sediments at different depths of a sediment core  are taken at physically separate depths in the core. Thus, the order of the indices cannot be flipped, and must be strictly decreasing/increasing.

See also: [`StartToEnd`](@ref)
