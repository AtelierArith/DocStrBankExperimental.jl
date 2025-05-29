```
calculatesignal_gbloch_ide(α, TRF, TR, ω0, B1, m0s, R1f, R2f, Rx, R1s, T2s[; grad_list, Ncyc=2, output=:complexsignal])
```

Calculate the signal or magnetization evolution with the full generalized Bloch model assuming a super-Lorentzian lineshape (slow).

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
  * `greens=(greens_superlorentzian, dG_o_dT2s_x_T2s_superlorentzian)`: Tuple of a Greens function `G(κ) = G((t-τ)/T2s)` and its partial derivative wrt. T2s, multiplied by T2s `∂G((t-τ)/T2s)/∂T2s * T2s`. This package supplies the three Greens functions `greens=(greens_superlorentzian, dG_o_dT2s_x_T2s_superlorentzian)` (default), `greens=(greens_lorentzian, dG_o_dT2s_x_T2s_lorentzian)`, and `greens=(greens_gaussian, dG_o_dT2s_x_T2s_gaussian)`

# Examples

```jldoctest
julia> calculatesignal_gbloch_ide(ones(100)*π/2, ones(100)*5e-4, 4e-3, 0, 1, 0.2, 0.3, 15, 20, 2, 10e-6)
100×1 Matrix{ComplexF64}:
  -0.007966316445310092 + 0.0im
  0.0012590590420428192 - 0.0im
  -0.006088855588249714 + 0.0im
   0.002418738940913121 - 0.0im
  -0.004361339394954344 + 0.0im
  0.0034891358222515403 - 0.0im
 -0.0027633710605856443 + 0.0im
   0.004483217942995644 - 0.0im
 -0.0012812573504847747 + 0.0im
    0.00540885403652597 - 0.0im
                        ⋮
   0.017760808273166742 - 0.0im
    0.01757611897551337 + 0.0im
    0.01781395094611674 - 0.0im
    0.01764385633643124 + 0.0im
   0.017863575856212052 - 0.0im
   0.017706926034820797 + 0.0im
   0.017909914934264796 - 0.0im
    0.01776565037417232 + 0.0im
   0.017953184893722073 - 0.0im

julia> calculatesignal_gbloch_ide(ones(100)*π/2, ones(100)*5e-4, 4e-3, 0, 1, 0.2, 0.3, 15, 20, 2, 10e-6; grad_list=(grad_R1f(), grad_T2s()), output=:realmagnetization)
100×15 transpose(::Matrix{Float64}) with eltype Float64:
 -0.00796627   0.0   0.000637773  …   0.0   -10.8757  -335.26   0.0
  0.00125903  -0.0  -0.00700671      -0.0   125.882   -326.977  0.0
 -0.00608882   0.0   0.00185086       0.0   -30.4187  -317.56   0.0
  0.00241873  -0.0  -0.00520622      -0.0    96.1776  -309.906  0.0
 -0.00436133   0.0   0.00296471       0.0   -47.5803  -302.948  0.0
  0.003489    -0.0  -0.00354518   …  -0.0    69.5148  -298.697  0.0
 -0.00276366   0.0   0.00399588       0.0   -62.8453  -294.886  0.0
  0.00448273  -0.0  -0.00200673      -0.0    45.3179  -292.783  0.0
 -0.00128187   0.0   0.00495478       0.0   -76.6573  -290.321  0.0
  0.00540814  -0.0  -0.000578836     -0.0    23.1756  -289.245  0.0
  ⋮                               ⋱
  0.0177563   -0.0   0.0175372       -0.0  -290.779   -349.855  0.0
  0.0175716    0.0   0.0177845        0.0  -295.347   -350.002  0.0
  0.0178094   -0.0   0.0176073       -0.0  -292.44    -350.163  0.0
  0.0176393    0.0   0.0178359        0.0  -296.668   -350.3    0.0
  0.017859    -0.0   0.0176727    …  -0.0  -294.001   -350.451  0.0
  0.0177024    0.0   0.0178838        0.0  -297.914   -350.579  0.0
  0.0179053   -0.0   0.0177335       -0.0  -295.467   -350.72   0.0
  0.0177611    0.0   0.0179286        0.0  -299.09    -350.84   0.0
  0.0179486   -0.0   0.0177902       -0.0  -296.845   -350.972  0.0
```
