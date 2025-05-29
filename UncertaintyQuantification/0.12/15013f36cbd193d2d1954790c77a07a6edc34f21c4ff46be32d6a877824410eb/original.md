```
EmpiricalPSD(ω::AbstractVector{<:Real}, p::AbstractVector{<:Real}) -> EmpiricalPSD
```

Constructs an `EmpiricalPSD` instance with the given angular frequencies and manually provided power spectral density values.

# Arguments

  * `ω::AbstractVector{<:Real}`: A vector of angular frequencies.
  * `p::AbstractVector{<:Real}`: A vector of power spectral density values corresponding to the frequencies in `ω`.

# Returns

A discretized `EmpiricalPSD` instance with manually pre-specified provided power spectral density values.

# Example

```julia
w = 0:0.1:10
p_values = rand(length(w))  # Example empirical PSD values
emp_psd = EmpiricalPSD(w, p_values)
```
