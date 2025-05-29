```
DirectInterpolation{D}(data::AbstractArray, ts::AbstractVector{<:Integer})
```

A lightweight interpolation type that provides the same interface as DataInterpolations.jl but uses direct indexing instead of interpolation algorithms.

# Arguments

  * `data::AbstractArray`: The data array to be interpolated
  * `ts::AbstractVector{<:Integer}`: The time points corresponding to the data

# Interface

Implements the same callable interface as DataInterpolations.jl interpolation types:

  * `(interp::DirectInterpolation)(t)`: Get the value at time `t`

# Implementation Details

Rather than performing interpolation calculations, this type simply returns the data value at the ceiling of the requested time index. For non-integer time points `t`, it uses `ceil(Int, t)` to get the next integer index.

# Example

```julia
data = rand(100)
ts = 1:100
interp = DirectInterpolation(data, ts)
value = interp(1.7)  # Returns data[2] (ceiling of 1.7)
```
