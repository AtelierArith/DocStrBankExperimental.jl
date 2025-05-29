```
calculatesignal_linearapprox(α, TRF, TR, ω0, B1, m0s, R1f, R2f, Rx, R1s, T2s, R2slT[; grad_list=(undef,), rfphase_increment=[π], m0=:periodic, output=:complexsignal, isInversionPulse = [true; falses(length(α)-1)]])
```

Calculate the signal or magnetization evolution with the linear approximation of the generalized Bloch model assuming a super-Lorentzian lineshape.

The simulation assumes a sequence of rectangular RF-pulses with varying flip angles α and RF-pulse durations TRF, but a fixed repetition time TR. Further, it assumes balanced gradient moments.

# Arguments

  * `α::Vector{Real}`: Array of flip angles in radians
  * `TRF::Vector{Real}`: Array of the RF-pulse durations in seconds
  * `TR::Real`: Repetition time in seconds
  * `ω0::Real`: Off-resonance frequency in rad/s
  * `B1::Real`: Normalized transmit B1 field, i.e. B1 = 1 corresponds to a well-calibrated B1 field
  * `m0s::Real`: Fractional size of the semi-solid pool; should be in range of 0 to 1
  * `R1f::Real`: Longitudinal relaxation rate of the free pool in 1/seconds
  * `R2f::Real`: Transversal relaxation rate of the free pool in 1/seconds
  * `Rx::Real`: Exchange rate between the two spin pools in 1/seconds
  * `R1f::Real`: Longitudinal relaxation rate of the semi-solid pool in 1/seconds
  * `T2s::Real`: Transversal relaxation time of the semi-solid pool in seconds
  * `R2slT::NTuple{3, Function}`: Tuple of three functions: R2sl(TRF, ω1, B1, T2s), dR2sldB1(TRF, ω1, B1, T2s), and R2sldT2s(TRF, ω1, B1, T2s). Can be generated with [`precompute_R2sl`](@ref)

Optional:

  * `grad_list=(undef,)`: Tuple that specifies the gradients that are calculated; the vector elements can either be `undef` for no gradient, or any subset/order of `grad_list=(grad_m0s(), grad_R1f(), grad_R2f(), grad_Rx(), grad_R1s(), grad_T2s(), grad_ω0(), grad_B1())`; the derivative wrt. to apparent `R1a = R1f = R1s` can be calculated with `grad_R1a()`
  * `rfphase_increment=[π]::Vector{Real}`: Increment of the RF phase between consecutive pulses. The default value `π`, together with $ω0=0$ corresponds to the on-resonance condition. When more than one value is supplied, their resulting signal is stored along the second dimension of the output array.
  * `m0=:periodic`: With the default keyword `:periodic`, the signal and their derivatives are calculated assuming $m(0) = -m(T)$, where `T` is the duration of the RF-train. With the keyword :thermal, the magnetization $m(0)$ is initialized with thermal equilibrium `[xf, yf, zf, xs, zs] = [0, 0, 1-m0s, 0, m0s]`, followed by a α[1]/2 - TR/2 prep pulse; and with the keyword `:IR`, this initialization is followed an inversion pulse of duration `TRF[1]`, (set `α[1]=π`) and a α[2]/2 - TR/2 prep pulse.
  * `preppulse=false`: if `true`, a `α/2 - TR/2` preparation is applied. In the case of `m0=:IR`, it is applied after the inversion pulse based on `α[2]`, otherwise it is based on `α[1]`
  * `output=:complexsignal`: The default keywords triggers the function to output a complex-valued signal (`xf + 1im yf`); the keyword `output=:realmagnetization` triggers an output of the entire (real valued) vector `[xf, yf, zf, xs, zs, 1]`
  * `isInversionPulse::Vector{Bool}`: Indicates all inversion pulses; must have the same length as α; the `default = [true; falses(length(α)-1)]` indicates that the first pulse is an inversion pulse and all others are not

# Examples

```jldoctest
julia> R2slT = precompute_R2sl();


julia> calculatesignal_linearapprox(ones(100)*π/2, ones(100)*5e-4, 4e-3, 0, 1, 0.1, 1, 15, 30, 6.5, 10e-6, R2slT)
100×1×1 Array{ComplexF64, 3}:
[:, :, 1] =
  -0.029305987774458163 - 0.0im
   0.004329424678273618 + 0.0im
  -0.022761409373843695 + 0.0im
   0.008280330224850314 + 0.0im
  -0.016751305727868086 + 0.0im
   0.011921649143708494 + 0.0im
   -0.01119057989041819 + 0.0im
   0.015305608440952356 + 0.0im
 -0.0060267918180664974 + 0.0im
   0.018463027499697613 + 0.0im
                        ⋮
   0.061531473509660414 + 0.0im
    0.06081400768357244 + 0.0im
     0.0617257515931871 + 0.0im
   0.061064216222629225 + 0.0im
     0.0619074570531536 + 0.0im
    0.06129750535994419 + 0.0im
   0.062077399758002534 + 0.0im
   0.061515021919442275 + 0.0im
    0.06223633770306246 + 0.0im
```
