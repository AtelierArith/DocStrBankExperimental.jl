```
get_measurement(data::QKData{T,N}, t::Int) where {T<:Real, N}
```

Extract measurement at time t from QKData.  For vector data returns a scalar, for matrix data returns a vector.

# Arguments

  * `data::QKData{T,N}`: Data structure
  * `t::Int`: Time index (1-based)

# Returns

  * For N=1: Single measurement Y[t]
  * For N=2: Vector of measurements Y[:,t]

# Throws

  * ArgumentError if t is out of bounds
