```
ZernikeCoefficients(n::Integer; T::Type{<:Real}=Float64)
```

Construct ZernikeCoefficients with `n` terms initialized to standard values.

# Arguments

  * `n`: Number of Zernike terms
  * `T`: Numeric type for coefficients (default: Float64)

# Returns

  * `ZernikeCoefficients` with magnitude[1] = 1 and all other terms zero

# Examples

```julia
# Create coefficients for first 15 Zernike terms
zc = ZernikeCoefficients(15)

# Create coefficients with specific numeric type
zc = ZernikeCoefficients(10, T=Float32)
```
