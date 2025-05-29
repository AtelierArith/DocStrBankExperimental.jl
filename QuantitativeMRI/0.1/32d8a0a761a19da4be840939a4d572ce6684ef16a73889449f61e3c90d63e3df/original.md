```
T2Fit_EpgNoise(ima::Array{T,4}, T1,TE,ETL,x0::Vector{Float64}) where T<:Real
```

Fit the relaxation parameters T2 of a Multi-Spin Multi-Echo sequence with constant $\Delta TE$ and refocusing pulse. EPG is computed with MRIReco functions. In order to compute the gaussian noise standard deviation you need to know the number of coils `l` and apply the following equation :

$\sigma_g = \frac{\sigma}{\sqrt{2L}}$

# Arguments

  * `ima::Array{T,N}`: image where the echoes are in the last dimension
  * `t::Union{Vector{<:Real},StepRange{<:Real,<:Real}}`: times vector in ms
  * `T1`: T1 relaxation time
  * `TE`: Echo Time
  * `ETL`: Echo Train Length

# Keywords

# Returns fitted maps with format (x,y,z, M0,T2,delta (b1), Noise)

# Bibliography

## Noise

  * Cárdenas-Blanco A, Tejos C, Irarrazaval P, Cameron I. Noise in magnitude magnetic resonance images. Concepts Magn Reson Part A [Internet]. 2008 Nov;32A(6):409–16. Available from: http://doi.wiley.com/10.1002/cmr.a.20124
  * Feng Y, He T, Gatehouse PD, Li X, Harith Alam M, Pennell DJ, et al. Improved MRI R 2 * relaxometry of iron-loaded liver with noise correction. Magn Reson Med [Internet]. 2013 Dec;70(6):1765–74. Available from: http://doi.wiley.com/10.1002/mrm.24607

## EPG

  * MRIReco.jl implementation
