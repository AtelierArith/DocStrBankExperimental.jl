```
HW_index(anorm::AbstractVector; p_left = 0.99)
HW_index(anorm::AbstractVector, dates; p_left=0.99)
```

Compute the HW index for a given anomaly vector `anorm`.

# Arguments

  * `anorm::AbstractVector`: A vector of anomaly scores.
  * `p_left::Float64=0.99`: The probability of false positives.

# Returns

A named tuple with the following fields:

  * `duration::Int`: The duration of the anomaly.
  * `frequency::Int`: The number of anomaly events.
  * `intensity::Float64`: The maximum anomaly score.
  * `volume::Float64`: The sum of anomaly scores.
  * `PR::Float64`: The probability of detection.
  * `FAR::Float64`: The false alarm rate.

# Example

```julia
julia> HW_index([0.1, 0.2, 0.3, 0.2, 0.1, 0, -0.1, 0.1, 0.2, 0.3])
(duration = 9, frequency = 2, intensity = 0.3, volume = 1.5, PR = 89.99999999999993, FAR = 0.9888888888888889)

julia> HW_index([-1, -1])
(duration = 0, frequency = 0, intensity = NaN, volume = NaN, PR = NaN, FAR = NaN)
```

# References

1. Kong, D., Gu, X., Li, J., Ren, G., & Liu, J. (2020). Contributions of Global Warming and Urbanization to the Intensification of Human‐Perceived Heatwaves Over China. Journal of Geophysical Research: Atmospheres, 125(18). [https://doi.org/10.1029/2019JD032175](https://doi.org/10.1029/2019JD032175)
