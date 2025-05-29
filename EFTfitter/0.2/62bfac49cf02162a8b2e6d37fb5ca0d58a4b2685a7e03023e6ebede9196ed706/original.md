````
to_correlation_matrix(
    measurements::NamedTuple{<:Any, <:Tuple{Vararg{AbstractMeasurement}}},
    correlations::Tuple{Symbol,Symbol, Union{<:Real, Array{<:Real, 2}}}...
)

Returns a `Matrix{Float64}` as the correlation matrix for the measurements with all diagonal-elements being unity.
The correlations are specified by passing tuples of two `Symbols` (the keys of the `Measurements`) with a value or matrix for the correlation coefficients.
If the matrix is not positive-definite, a warning is shown but the matrix is still returned.

Example:
```julia
dist_corr = [1.0 0.5 0.0;
             0.5 1.0 0.0;
             0.0 0.0 1.0]

another_corr_matrix = to_correlation_matrix(
    measurements,
    (:Meas1, :Meas2, 0.4), 
    (:Meas1, :MeasDist, 0.1), 
    (:MeasDist, :MeasDist, dist_corr), 
    (:MeasDist_bin2, :MeasDist_bin3, 0.3),
)
```
````
