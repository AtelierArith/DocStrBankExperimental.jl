```
intermittent_correlation(
    data::AbstractVector; 
    maxdelta = length(data) ÷ 10, 
    types::Function = x -> true,
    show_progress::Bool = true,
)
```

Calculate the intermittent correlation function of a time series. That is, computes the probability of finding a value of the same type at a step `i + delta` in the time series, given that it was present in step `i`.

Returns an `OffsetArray` with indices `0:maxdelta`, where the value at position `0` is `1.0`, corresponding to the normalized count of events. 

# Arguments

  * `data::AbstractVector`: The time series to be analyzed.
  * `maxdelta::Integer`: The maximum delta-step to be considered. Defaults to  `length(data) ÷ 10`.
  * `types` (optional): A function that returns `true` for the types of data  that should be considered. Defaults to all data, i. e. `x -> true`. For   example, to ignore `0` values, use `types = x -> x != 0`.
  * `show_progress::Bool`: Show progress bar. Defaults to `true`.

# Examples

Here we produce a time-series of 10,000 elements, as a sequence of  1's and 0's (`[1, 0, 1, 0, ...]`), and calculate the intermittent correlation function. The probability of finding the same number (0 or 1) after odd steps is 0, and the probability of finding the same number after even steps is 1.

```jldoctest
julia> using MolSimToolkit

julia> data = [ mod(i,2) for i in 1:10^4 ];

julia> intermittent_correlation(data; maxdelta=4, show_progress=false)
5-element OffsetArray(::Vector{Float64}, 0:4) with eltype Float64 with indices 0:4:
 1.0
 0.0
 1.0
 0.0
 1.0

julia> intermittent_correlation(data; maxdelta=4, types = x -> x != 0, show_progress=false)
5-element OffsetArray(::Vector{Float64}, 0:4) with eltype Float64 with indices 0:4:
 1.0
 0.0
 1.0
 0.0
 1.0
```

In the second run, we have ignored the `0` values, and the result is the same,  because here the correlations of the `1` values are the same as the correlations of the `0` values.

!!! compat
    This function was added in version 1.9.0 of MolSimToolkit. The `types` argument was added in version 1.10.0 and the `show_progress` argument in version 1.28.0.

