```
T2Fit_Exp(ima::Array{T,N},t::AbstractVector{T},p0=nothing) where {T<:Real,N}
```

Fit the relaxation parameters T2 with the equation : $S(t) = M_0 \exp(-\frac{t}{T2})$.

# Arguments

  * `ima::Array{T,N}`: image with dimension [x,...,t]. Last dimensions -> temporal dimension
  * `t::AbstractVector{<:Real}`: times vector in ms
  * `p0=nothing`: starting values for fit, if empty p0=[maximum(ima),30]

# Keywords

  * `removePoint::Bool=true`: remove the first point before fitting

# Returns

  * fit_params : parameter maps

      * M₀ maps (no unit)
      * T₂ maps (ms)
