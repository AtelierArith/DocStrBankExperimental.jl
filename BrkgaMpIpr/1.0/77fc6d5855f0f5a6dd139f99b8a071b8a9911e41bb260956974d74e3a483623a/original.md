```
kendall_tau_distance(vector1::Array{Float64, 1},
                     vector2::Array{Float64, 1};
                     stop_immediately::Bool = false)::Float64

kendall_tau_distance(vector1::SubArray{Float64, 1},
                     vector2::SubArray{Float64, 1};
                     stop_immediately::Bool = false)::Float64
```

Compute the [Kendall Tau distance](https://en.wikipedia.org/wiki/Kendall_tau_distance) between two vectors.

!!! note
    This function may be more appropriated to permutation chromosome representations.


# Arguments

  * `vector1::Array{Float64, 1}`: the first vector.
  * `vector2::Array{Float64, 1}`: the second vector.
  * `stop_immediately::Bool = false`: if `true`, stop the computation immediately after find a difference.

# Throws

  * `ArgumentError`: if `vector1` and `vector2` have different sizes.
