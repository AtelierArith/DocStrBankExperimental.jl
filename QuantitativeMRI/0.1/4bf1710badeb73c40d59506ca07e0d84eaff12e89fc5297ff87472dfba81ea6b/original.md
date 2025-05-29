```
T2Fit_ExpNoise(ima::Array{T,N},t::AbstractVector{<:Real},p0=nothing; kwargs...) where {T<:Real,N}
```

Fit the relaxation parameters T2 with the equation : $S(t) = \sqrt{(M_0 \exp(-\frac{t}{T2}))^2 + 2 L \sigma_g^2}$ where L est le nombre de canaux, et $\sigma_g$ le bruit gaussien sur les image

# Arguments

  * `ima::Array{T,N}`: image with dimension [x,...,t]. Last dimensions -> temporal dimension
  * `t::AbstractVector{<:Real}`: times vector in ms
  * `p0=nothing`: starting values for fit, if empty p0=[maximum(ima),30,maximum(ima)*0.1]

# Keywords

  * `removePoint::Bool=true`: remove the first point before fitting
  * `L::Int=1`: Number of coil elements

# Returns

  * fit_params : parameter maps

      * M₀ maps (no unit)
      * T₂ maps (ms)
      * Noise maps (no unit)
  * fit_vec : fit objects for each pixels

# Bibliography

  * Cárdenas-Blanco A, Tejos C, Irarrazaval P, Cameron I. Noise in magnitude magnetic resonance images. Concepts Magn Reson Part A [Internet]. 2008 Nov;32A(6):409–16. Available from: http://doi.wiley.com/10.1002/cmr.a.20124
  * Feng Y, He T, Gatehouse PD, Li X, Harith Alam M, Pennell DJ, et al. Improved MRI R 2 * relaxometry of iron-loaded liver with noise correction. Magn Reson Med [Internet]. 2013 Dec;70(6):1765–74. Available from: http://doi.wiley.com/10.1002/mrm.24607
