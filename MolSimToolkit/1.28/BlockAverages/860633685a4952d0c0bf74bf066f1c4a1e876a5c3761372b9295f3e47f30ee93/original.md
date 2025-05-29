```
block_average(
    x::AbstractVector{T};
    by = mean,
    min_block_size::Integer = 1,
    max_block_size::Integer = length(x),
    lags::Union{Nothing,AbstractVector{<:Integer}} = nothing,
) where {T<:Real}
```

This function peforms some convergence analysis for a property computed from a series of data, typically a time-series.  The data is given in vector `x`, and `by` defines the property to be estimated, typically, and by default, the mean value.

Two analyses are performed: a block averaging, in which the data is split in to blocks, and the mean value (or `by` value) in each block is computed idependently. The output will contain the worst estimate obtained for all blocks, and the standard error of the estimates, as a function of the block size. 

Finally, the autocorrelation function of the data is computed, and a single exponential is fitted, to obtain the characteristic time of the decay of the correlation. 

The output will be a structure of type `BlockAverageData{T}`. See the corresponding help entry for more information.

All results can be plot with a convenience function `BlockAverage.plot`

The `lags` keyword can be tuned to define the range of intervals and length of the autocorrelation calculation, with important implications to the exponential fit and correlation curve shape. See the `StatsBase.autocor` help for  further information.

## Example

```julia-repl
julia> using MolSimToolkit

julia> x = BlockAverages.test_data(10^6); # example data generator

julia> b = block_average(x, lags=0:100:10^5)
-------------------------------------------------------------------
BlockAverageData{Float64}
-------------------------------------------------------------------
Estimated value (mean by default) = -0.13673023261452855
Length of data series: 1000000

Block sizes: [1, 2, ..., 500000, 1000000]

Maximum standard error (error, block size): (0.23264202379194165, 500000)

Deviations in last 3 blocks:
         percentual: [-349.5348293165444, -170.1467329817311, -0.0]  
           absolute: [0.47791978519330647, 0.23264202379194168, 0.0]  

Autocorrelation is first zero with lag: 16400
Characteristic time of autocorrelation decay: 
        as fraction of series length: 0.0037856443348888848
                            absolute: 3785.6443348888847
-------------------------------------------------------------------

julia> using Plots

julia> plot(b) # creates a plot with the results

```
