```
qM = fit_gBloch(data, α, TRF, TR;
    reM0 = (-Inf,   1,  Inf),
    imM0 = (-Inf,   0,  Inf),
    m0s  = (   0, 0.2,    1),
    R1f  = (   0, 0.3,  Inf),
    R2f  = (   0,  15,  Inf),
    Rx   = (   0,  20,  Inf),
    R1s  = (   0,   3,  Inf),
    T2s  = (8e-6,1e-5,12e-6),
    ω0   = (-Inf,   0,  Inf),
    B1   = (   0,   1,  1.5),
    R1a  = (   0, 0.7,  Inf),
    u=1,
    fit_apparentR1=false,
    show_trace=false,
    maxIter=100,
    R2slT = precompute_R2sl(TRF_min=minimum(TRF), TRF_max=maximum(TRF), T2s_min=minimum(T2s), T2s_max=maximum(T2s), ω1_max=maximum(α ./ TRF), B1_max=maximum(B1)),
    )
```

Fit the generalized Bloch model for a train of RF pulses and balanced gradient moments to `data`.

# Arguments

  * `data::Vector{Number}`: Array of measured data points, either in the time or a compressed domain (cf. `u`)
  * `α::Vector{Real}`: Array of flip angles in radians; can also be a `Vector{Vector{Real}}` which simulates each RF pattern and concatenates the signals of each simulation
  * `TRF::Vector{Real}`: Array of the RF-pulse durations in seconds (or `Vector{Vector{Real}}` if `α::Vector{Vector{Real}}``)
  * `TR::Real`: Repetition time in seconds
  * `ω0::Real`: Off-resonance frequency in rad/s

# Optional Keyword Arguments:

  * `reM0::Union{Real, Tuple{Real, Real, Real}}`: Real part of `M0`; either fixed value as a `Real` or fit limits thereof as a `Tuple` with the elements `(min, start, max)`
  * `imM0::Union{Real, Tuple{Real, Real, Real}}`: Imaginary part of `M0`; either fixed value as a `Real` or fit limits thereof as a `Tuple` with the elements `(min, start, max)`
  * `m0s::Union{Real, Tuple{Real, Real, Real}}`: Fractional size of the semi-solid pool (should be in range of 0 to 1); either fixed value as a `Real` or fit limits thereof as a `Tuple` with the elements `(min, start, max)`
  * `R1f::Union{Real, Tuple{Real, Real, Real}}`: Longitudinal relaxation rate of the free pool in 1/s; only used in combination with `fit_apparentR1=false`; either fixed value as a `Real` or fit limits thereof as a `Tuple` with the elements `(min, start, max)`
  * `R2f::Union{Real, Tuple{Real, Real, Real}}`: Transversal relaxation rate of the free pool in 1/s; either fixed value as a `Real` or fit limits thereof as a `Tuple` with the elements `(min, start, max)`
  * `Rx::Union{Real, Tuple{Real, Real, Real}}`: Exchange rate between the two spin pools in 1/s; either fixed value as a `Real` or fit limits thereof as a `Tuple` with the elements `(min, start, max)`
  * `R1s::Union{Real, Tuple{Real, Real, Real}}`: Longitudinal relaxation rate of the semi-solid pool in 1/s; only used in combination with `fit_apparentR1=false`; either fixed value as a `Real` or fit limits thereof as a `Tuple` with the elements `(min, start, max)`
  * `T2s::Union{Real, Tuple{Real, Real, Real}}`: Transversal relaxation time of the semi-solid pool in s; either fixed value as a `Real` or fit limits thereof as a `Tuple` with the elements `(min, start, max)`
  * `ω0::Union{Real, Tuple{Real, Real, Real}}`: Off-resonance frequency in rad/s; either fixed value as a `Real` or fit limits thereof as a `Tuple` with the elements `(min, start, max)`
  * `B1::Union{Real, Tuple{Real, Real, Real}}`: Normalized transmit B1 field, i.e. B1 = 1 corresponds to a well-calibrated B1 field; either fixed value as a `Real` or fit limits thereof as a `Tuple` with the elements `(min, start, max)`
  * `R1a::Union{Real, Tuple{Real, Real, Real}}`: Apparent longitudinal relaxation rate in 1/s; only used in combination with `fit_apparentR1=true`; either fixed value as a `Real` or fit limits thereof as a `Tuple` with the elements `(min, start, max)`
  * `u::Union{Number, Matrix}`: Compression matrix that transform the simulated time series to a series of coefficients. Set to `1` by default to enable the fitting in the time domain
  * `fit_apparentR1::Bool`: Switch between fitting `R1f` and `R1s` separately (`false`; default) and an apparent `R1a = R1f = R1s` (`true`)
  * `show_trace::Bool`: print output during the optimization; `default=false`
  * `maxIter::Int`: Maximum number of iteration; `default=100`
  * `R2slT::NTuple{3, Function}`: Tuple of three functions: R2sl(TRF, ω1, B1, T2s), dR2sldB1(TRF, ω1, B1, T2s), and R2sldT2s(TRF, ω1, B1, T2s). By default generated with [`precompute_R2sl`](@ref)

# Examples

c.f. [Non-Linear Least Square Fitting](@ref)
