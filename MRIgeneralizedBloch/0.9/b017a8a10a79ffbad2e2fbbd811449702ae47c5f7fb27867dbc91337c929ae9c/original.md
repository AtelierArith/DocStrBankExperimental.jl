```
apply_hamiltonian_sled!(∂m∂t, m, p, t)
```

Apply Sled's Hamiltonian to `m` and write the resulting derivative wrt. time into `∂m∂t`.

# Arguments

  * `∂m∂t::Vector{<:Real}`: Vector of length 1 describing to derivative of `m` wrt. time; this vector can contain any value, which is replaced by `H * m`
  * `m::Vector{<:Real}`: Vector of length 1 describing the `zs` magnetization
  * `p::NTuple{6 or 10, Any}`: `(ω1, B1, ω0, R1s, T2s, g)` for a simulating an isolated semi-solid pool or `(ω1, B1, ω0, m0s, R1f, R2f, Rx, R1s, T2s, g)` for simulating a coupled spin system; with

      * `ω1::Real`: Rabi frequency in rad/s (rotation about the y-axis) or
      * `ω1(t)::Function`: Rabi frequency in rad/s as a function of time for shaped RF-pulses
      * `B1::Real`: B1 scaling normalized so that `B1=1` corresponds to a perfectly calibrated RF field
      * `ω0::Real`: Larmor or off-resonance frequency in rad/s (is only used for the free spin pool)
      * `R1f::Real`: Longitudinal spin relaxation rate of the free pool in 1/seconds
      * `R2f::Real`: Transversal spin relaxation rate of the free pool in 1/seconds
      * `R1s::Real`: Longitudinal spin relaxation rate of the semi-solid in 1/seconds
      * `Rx::Real`: Exchange rate between the two pools in 1/seconds
      * `T2s::Real`: Transversal spin relaxation time in seconds
      * `g::Function`: Green's function of the form `G(κ) = G((t-τ)/T2s)`
  * `t::Real`: Time in seconds

# Examples

```jldoctest
julia> using DifferentialEquations


julia> α = π/2;

julia> TRF = 100e-6;

julia> ω1 = α/TRF;

julia> B1 = 1;

julia> ω0 = 0;

julia> R1s = 2;

julia> T2s = 10e-6;

julia> G = interpolate_greens_function(greens_superlorentzian, 0, TRF / T2s);

julia> m0 = [1];

julia> sol = solve(ODEProblem(apply_hamiltonian_sled!, m0, (0, TRF), (ω1, 1, ω0, R1s, T2s, G)), Tsit5())
retcode: Success
Interpolation: specialized 4th order "free" interpolation
t: 3-element Vector{Float64}:
 0.0
 7.475414666720001e-5
 0.0001
u: 3-element Vector{Vector{Float64}}:
 [1.0]
 [0.6313928231811967]
 [0.4895365449661915]

julia> using Plots

julia> plot(sol, labels=["zs"], xlabel="t (s)", ylabel="m(t)");



```
