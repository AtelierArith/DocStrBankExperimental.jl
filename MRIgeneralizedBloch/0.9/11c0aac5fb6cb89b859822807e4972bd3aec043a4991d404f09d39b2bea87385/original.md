```
apply_hamiltonian_gbloch!(∂m∂t, m, mfun, p, t)
```

Apply the generalized Bloch Hamiltonian to `m` and write the resulting derivative wrt. time into `∂m∂t`.

# Arguments

  * `∂m∂t::Vector{Real}`: Vector describing to derivative of `m` wrt. time; this vector has to be of the same size as `m`, but can contain any value, which is replaced by `H * m`
  * `m::Vector{Real}`: Vector the spin ensemble state of the form `[xf, yf, zf, zs, 1]` if now gradient is calculated or of the form `[xf, yf, zf, zs, 1, ∂xf/∂θ1, ∂yf/∂θ1, ∂zf/∂θ1, ∂zs/∂θ1, 0, ..., ∂xf/∂θn, ∂yf/∂θn, ∂zf/∂θn, ∂zs/∂θn, 0]` if n derivatives wrt. `θn` are calculated
  * `mfun`: History function; can be initialized with `mfun(p, t; idxs=nothing) = typeof(idxs) <: Real ? 0.0 : zeros(5n + 5)` for n gradients, and is then updated by the delay differential equation solvers
  * `p::NTuple{6,Any}`: `(ω1, B1, ω0, R1s, T2s, g)` or
  * `p::NTuple{6,Any}`: `(ω1, B1,  φ, R1s, T2s, g)` or
  * `p::NTuple{10,Any}`: `(ω1, B1, ω0, m0s, R1f, R2f, Rx, R1s, T2s, g)` or
  * `p::NTuple{10,Any}`: `(ω1, B1,  φ, m0s, R1f, R2f, Rx, R1s, T2s, g)` or
  * `p::NTuple{12,Any}`: `(ω1, B1, ω0, m0s, R1f, R2f, Rx, R1s, T2s, g, dG_o_dT2s_x_T2s, grad_list)` or
  * `p::NTuple{12,Any}`: `(ω1, B1, ω0, m0s, R1f, R2f, Rx, R1s, T2s, g, dG_o_dT2s_x_T2s, grad_list)` with the following entries

      * `ω1::Real`: Rabi frequency in rad/s (rotation about the y-axis) or
      * `ω1(t)::Function`: Rabi frequency in rad/s as a function of time for shaped RF-pulses
      * `B1::Real`: B1 scaling normalized so that `B1=1` corresponds to a perfectly calibrated RF field
      * `ω0::Real`: Larmor or off-resonance frequency in rad/s or
      * `φ::Function`: RF-phase in rad as a function of time for frequency/phase-sweep pulses (works only in combination with `ω1(t)::Function`)
      * `m0s::Real`: Fractional semi-solid spin pool size in the range of 0 to 1
      * `R1f::Real`: Longitudinal spin relaxation rate of the free pool in 1/seconds
      * `R2f::Real`: Transversal spin relaxation rate of the free pool in 1/seconds
      * `Rx::Real`: Exchange rate between the two pools in 1/seconds
      * `R1s::Real`: Longitudinal spin relaxation rate of the semi-solid pool in 1/seconds
      * `T2s::Real`: Transversal spin relaxation time of the semi-solid pool in seconds
      * `g::Function`: Green's function of the form `G(κ) = G((t-τ)/T2s)`
      * `dG_o_dT2s_x_T2s::Function`: Derivative of the Green's function wrt. T2s, multiplied by T2s; of the form `dG_o_dT2s_x_T2s(κ) = dG_o_dT2s_x_T2s((t-τ)/T2s)`
      * `grad_list::Vector{grad_param}`: List of gradients to be calculated, i.e., any subset of `[grad_m0s(), grad_R1f(), grad_R2f(), grad_Rx(), grad_R1s(), grad_T2s(), grad_ω0(), grad_B1()]`; length of the vector must be n (cf. arguments `m` and `∂m∂t`); the derivative wrt. to apparent `R1a = R1f = R1s` can be calculated with `grad_R1a()`
  * `t::Real`: Time in seconds

Optional:

  * `pulsetype=:normal`: Use default for a regular RF-pulse; the option `pulsetype=:inversion` should be handled with care as it is only intended to calculate the saturation of the semi-solid pool and its derivative.

# Examples

```jldoctest
julia> using DifferentialEquations


julia> α = π/2;

julia> TRF = 100e-6;

julia> ω1 = α/TRF;

julia> B1 = 1;

julia> ω0 = 0;

julia> m0s = 0.2;

julia> R1f = 1/3;

julia> R2f = 15;

julia> R1s = 2;

julia> T2s = 10e-6;

julia> Rx = 30;

julia> G = interpolate_greens_function(greens_superlorentzian, 0, TRF / T2s);


julia> m0 = [0; 0; 1-m0s; m0s; 1];

julia> mfun(p, t; idxs=nothing) = typeof(idxs) <: Real ? 0.0 : zeros(5);

julia> sol = solve(DDEProblem(apply_hamiltonian_gbloch!, m0, mfun, (0, TRF), (ω1, B1, ω0, m0s, R1f, R2f, Rx, R1s, T2s, G)))
retcode: Success
Interpolation: specialized 4th order "free" interpolation, specialized 2nd order "free" stiffness-aware interpolation
t: 9-element Vector{Float64}:
 0.0
 1.375006182301112e-7
 1.512506800531223e-6
 8.042561696923577e-6
 2.107848894861101e-5
 3.9114182159866e-5
 6.26879358261189e-5
 9.147711414688425e-5
 0.0001
u: 9-element Vector{Vector{Float64}}:
 [0.0, 0.0, 0.8, 0.2, 1.0]
 [0.0017278806030763402, 0.0, 0.7999981340131751, 0.19999953350448, 1.0]
 [0.019004717382235078, 0.0, 0.7997742277135814, 0.19994357804868362, 1.0]
 [0.10079111348917136, 0.0, 0.7936248122939504, 0.19842287240368398, 1.0]
 [0.2600257867257624, 0.0, 0.7565529666157949, 0.1898191304278861, 1.0]
 [0.46104237829774064, 0.0, 0.6537239462232086, 0.16937683398576228, 1.0]
 [0.6661740376622253, 0.0, 0.44261209248221817, 0.13589311206074786, 1.0]
 [0.7923117772809817, 0.0, 0.10713073823030607, 0.09390260581965477, 1.0]
 [0.7994211188442756, 0.0, 0.0004403374305009168, 0.08214809659226184, 1.0]

julia> using Plots

julia> plot(sol, labels=["xf" "yf" "zf" "zs" "1"], xlabel="t (s)", ylabel="m(t)");




julia> dG_o_dT2s_x_T2s = interpolate_greens_function(dG_o_dT2s_x_T2s_superlorentzian, 0, TRF / T2s);


julia> grad_list = (grad_R2f(), grad_m0s());


julia> m0 = [0; 0; 1-m0s; m0s; 1; zeros(5*length(grad_list))];


julia> mfun(p, t; idxs=nothing) = typeof(idxs) <: Real ? 0.0 : zeros(5 + 5*length(grad_list));

julia> sol = solve(DDEProblem(apply_hamiltonian_gbloch!, m0, mfun, (0, TRF), (ω1, B1, ω0, m0s, R1f, R2f, Rx, R1s, T2s, G, dG_o_dT2s_x_T2s, grad_list)));




julia> plot(sol);


```
