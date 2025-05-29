```
calculatesignal_graham_ode(α, TRF, TR, ω0, B1, m0s, R1f, R2f, Rx, R1s, T2s[; grad_list, Ncyc=2, output=:complexsignal])
```

Calculate the signal or magnetization evolution with Graham's spectral model assuming a super-Lorentzian lineshape.

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
  * `R1s::Real`: Longitudinal relaxation rate of the semi-solid pool in 1/seconds
  * `T2s::Real`: Transversal relaxation time of the semi-solid pool in seconds

Optional:

  * `grad_list=()`: Tuple that specifies the gradients that are calculated; the Tuple can either be empty `()` for no gradient, or contain any subset/order of `grad_list=(grad_m0s(), grad_R1s(), grad_R2f(), grad_Rx(), grad_R1s(), grad_T2s(), grad_ω0(), grad_B1())`; the derivative wrt. to apparent `R1a = R1f = R1s` can be calculated with `grad_R1a()`
  * `Ncyc=2`: The magnetization is initialized with thermal equilibrium and then performed Ncyc times and only the last cycle is stored. The default value is usually a good approximation for antiperiodic boundary conditions. Increase the number for higher precision at the cost of computation time.
  * `output=:complexsignal`: The default keywords triggers the function to output a complex-valued signal (`xf + 1im yf`); the keyword `output=:realmagnetization` triggers an output of the entire (real valued) vector `[xf, yf, zf, xs, zs]`

# Examples

```jldoctest
julia> calculatesignal_graham_ode(ones(100)*π/2, ones(100)*5e-4, 4e-3, 0, 1, 0.2, 0.3, 15, 20, 2, 10e-6)
100×1 Matrix{ComplexF64}:
   -0.00807345119181352 + 0.0im
   0.001268643290482942 - 0.0im
 -0.0061786944372399285 + 0.0im
  0.0024358658178670984 - 0.0im
  -0.004437476277201395 + 0.0im
   0.003516464649840319 - 0.0im
 -0.0028315542520438736 + 0.0im
   0.004523902250379144 - 0.0im
 -0.0013422299483389865 + 0.0im
   0.005454562034842185 - 0.0im
                        ⋮
   0.018148222040953822 - 0.0im
    0.01795769661414946 + 0.0im
   0.018204860876661903 - 0.0im
    0.01802936310261858 + 0.0im
    0.01825782014256292 - 0.0im
   0.018096168912467753 + 0.0im
   0.018307337729977783 - 0.0im
    0.01815844450117701 + 0.0im
   0.018353636229654767 - 0.0im

julia> calculatesignal_graham_ode(ones(100)*π/2, ones(100)*5e-4, 4e-3, 0, 1, 0.2, 0.3, 15, 20, 2, 10e-6; grad_list=(grad_R1f(), grad_T2s()), output=:realmagnetization)
100×15 transpose(::Matrix{Float64}) with eltype Float64:
 -0.0080756    0.0   0.000643162  …   0.0   -10.4986  -323.634  0.0
  0.00126867  -0.0  -0.00710692      -0.0   123.078   -316.358  0.0
 -0.00618067   0.0   0.00186482       0.0   -29.4458  -307.862  0.0
  0.00243634  -0.0  -0.0052899       -0.0    94.1692  -300.821  0.0
 -0.00443746   0.0   0.00298646       0.0   -46.1422  -294.116  0.0
  0.00351386  -0.0  -0.00361718   …  -0.0    68.262   -289.421  0.0
 -0.00282882   0.0   0.00402793       0.0   -61.0236  -285.242  0.0
  0.00451808  -0.0  -0.00206741      -0.0    44.7888  -282.867  0.0
 -0.00133608   0.0   0.00499316       0.0   -74.4075  -280.79   0.0
  0.00544896  -0.0  -0.00062663      -0.0    23.2536  -280.148  0.0
  ⋮                               ⋱
  0.0181755   -0.0   0.0179431       -0.0  -285.071   -337.48   0.0
  0.0179911    0.0   0.0181963        0.0  -289.591   -337.634  0.0
  0.0182343   -0.0   0.018019        -0.0  -286.777   -337.804  0.0
  0.0180645    0.0   0.0182531        0.0  -290.964   -337.948  0.0
  0.0182893   -0.0   0.0180898    …  -0.0  -288.383   -338.106  0.0
  0.0181329    0.0   0.0183062        0.0  -292.261   -338.241  0.0
  0.0183407   -0.0   0.0181559       -0.0  -289.895   -338.39   0.0
  0.0181968    0.0   0.0183559        0.0  -293.488   -338.516  0.0
  0.0183888   -0.0   0.0182175       -0.0  -291.318   -338.656  0.0
```
