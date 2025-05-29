```julia
struct BlockAverageData{T}
```

Structure that contains the result of the block-average analysis of the sequence. 

`x` is the original data set. 

`xmean` is the property value computed for all data (usually the mean, but not necessarily)

`blocksize` is an array of block sizes, in which the data was split.  By default it goes from `1` to `length(x)`, with a number of points corresponding to the number of integer divisions of `length(x)`.

`xmean_maxerr`: The property is computed for each block, and the maximum error (difference between the property in the block and the average property) is stored in this array, for each blocks size. 

`xmean_stderr`: The standard error of the estimates of the property, meaning the standar  deviation of the estimates divided by the square root of the number of blocks. 

`autocor`: Is the autocorrelation function of the data, as a function of the lag. 

`lags`: Is the set of "time" lags for which the autocorrelation will be computed. Defined by the `lags` parameter of the `block_average` function, as a range. 

`tau`: The characteristic decay time of the autocorrelation function, as obtained by fitting of a single exponential, of the form `exp(-t/tau)` to the data. 
